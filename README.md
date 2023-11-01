 DATA_DIRECTORY = os.path.join(
        Path.home(),
        'chatterbot_corpus',
        'data'
    )
CORPUS_EXTENSION = 'yml' CORPUS_EXTENSION = 'yml'
@@ -38,6 +45,16 @@ def read_corpus(file_name):
    """    """
    Read and return the data from a corpus json file.
    Read and return the data from a corpus json file.
    """    """
    try:
        import yaml
    except ImportError:
        message = (
            'Unable to import "yaml".\n'
            'Please install "pyyaml" to enable chatterbot corpus functionality:\n'
            'pip3 install pyyaml'
        )
        raise OptionalDependencyImportError(message)

    with io.open(file_name, encoding='utf-8') as data_file:  
    with io.open(file_name, encoding='utf-8') as data_file:
        return yaml.safe_load(data_file)    
        return yaml.safe_load(data_file)
class OptionalDependencyImportError(ImportError):
    """
    An exception raised when a feature requires an optional dependency to be installed.
    """
    pass
from datetime import datetime from datetime import datetime
from chatterbot.logic import LogicAdapter from chatterbot.logic import LogicAdapter
from chatterbot.conversation import Statement from chatterbot.conversation import Statement
from chatterbot.exceptions import OptionalDependencyImportError
class TimeLogicAdapter(LogicAdapter): class TimeLogicAdapter(LogicAdapter):
@@ -18,7 +19,15 @@ class TimeLogicAdapter(LogicAdapter):
   def __init__(self, chatbot, **kwargs):
   def __init__(self, chatbot, **kwargs):
        super().__init__(chatbot, **kwargs)    
        super().__init__(chatbot, **kwargs)
        from nltk import NaiveBayesClassifier    
        try:
            from nltk import NaiveBayesClassifier
        except ImportError:
            message = (
                'Unable to import "nltk".\n'
                'Please install "nltk" before using the TimeLogicAdapter:\n'
                'pip3 install nltk'
            )
            raise OptionalDependencyImportError(message)


        self.positive = kwargs.get('positive', [      
        self.positive = kwargs.get('positive', [
          'what time is it',            'what time is it',

 DATA_DIRECTORY = os.path.join(
        Path.home(),
        'chatterbot_corpus',
        'data'
    )
CORPUS_EXTENSION = 'yml' CORPUS_EXTENSION = 'yml'
@@ -38,6 +45,16 @@ def read_corpus(file_name):
    """    """
    Read and return the data from a corpus json file.
    Read and return the data from a corpus json file.
    """    """
    try:
        import yaml
    except ImportError:
        message = (
            'Unable to import "yaml".\n'
            'Please install "pyyaml" to enable chatterbot corpus functionality:\n'
            'pip3 install pyyaml'
        )
        raise OptionalDependencyImportError(message)

    with io.open(file_name, encoding='utf-8') as data_file:  
    with io.open(file_name, encoding='utf-8') as data_file:
        return yaml.safe_load(data_file)    
        return yaml.safe_load(data_file)
class OptionalDependencyImportError(ImportError):
    """
    An exception raised when a feature requires an optional dependency to be installed.
    """
    pass
from datetime import datetime from datetime import datetime
from chatterbot.logic import LogicAdapter from chatterbot.logic import LogicAdapter
from chatterbot.conversation import Statement from chatterbot.conversation import Statement
from chatterbot.exceptions import OptionalDependencyImportError
class TimeLogicAdapter(LogicAdapter): class TimeLogicAdapter(LogicAdapter):
@@ -18,7 +19,15 @@ class TimeLogicAdapter(LogicAdapter):
   def __init__(self, chatbot, **kwargs):
   def __init__(self, chatbot, **kwargs):
        super().__init__(chatbot, **kwargs)    
        super().__init__(chatbot, **kwargs)
        from nltk import NaiveBayesClassifier    
        try:
            from nltk import NaiveBayesClassifier
        except ImportError:
            message = (
                'Unable to import "nltk".\n'
                'Please install "nltk" before using the TimeLogicAdapter:\n'
                'pip3 install nltk'
            )
            raise OptionalDependencyImportError(message)


        self.positive = kwargs.get('positive', [      
        self.positive = kwargs.get('positive', [
          'what time is it',            'what time is it',

