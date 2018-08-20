## AWS Polly Text-To-Speech PHP Library

Convert written text into natural-sounding audio in a variety of languages and voices.  
This package use [AWS Polly](https://aws.amazon.com/polly/) service.

---
### Using the Library

#### Installation

Intall library in PHP project using composer
```
composer require tbetool/aws-polly
```

#### Using Library

After installing the library, create `WatsonTts` object
```
$polly = new AwsPolly(
    'aws_key', 
    'aws_secret', 
    'aws_region'
);
```
AWS `key, secret` can be obtained by creating IAM user in AWS console. For more detail follow [Creating IAM for Polly](#).

#### Setting output path
Set absolute path of the directory where to save the output. You don't need to provide a file name as it will be auto generated.
```
$path = '/aboslute/path/to/directory';

$polly->setOutputPath($path);
```

**NOTE:** You can also pass output path with textToVoice() which will override this path

#### Convert Text to Speech
Pass text to convert to speech.
```
$file = $polly->textToVoice(
    'Hello World',
    $param
);
```
**$params** should be array and can have following content.
```
$param = [
    'language' => 'en-US',
    'voice' => 'Justin',
    'output_path' => '/absolute/file/path'
]
```
This will return the absolute path of the file created if text to speech conversion is successful, otherwise will throw Exception.

---
### Exception handling

Every function throws an Exception in case of any error/issue. Bind the code block within `try-catch` block to catch any exception occurred.

_Ex:_
```
try {
    $polly->textToVoice('Hello world');
} catch (Exception $exception) {
    echo $exception->getMessage();
}
```

---
### Other callable methods

##### Get supported languages
```
$polly->getLanguages();
```

_default:_ `en-US`
##### Get supported voices
```
$polly->getVoices();
``` 
_default:_ `Ivy`

---
### Supported language and voice list
list of supported language and voice strings

Country | language | voice | gender |
--- | --- | --- | --- | --- |
Danish | **da-DK** | **Mads** | male  |
|| **Naja** | female  |
Dutch | **nl-NL** | **Ruben** | male  |
|| **Lotte** | female  |
English (Australian) | **en-AU** | **Russell** | male  |
|| **Nicole** | female  |
English (British) | **en-GB** | **Brian** | male  |
|| **Amy** | female  |
|| **Emma** | female  |
English (Indian) | **en-IN** | **Aditi** | female  |
|| **Raveena** | female  |
English (US) | **en-US** | **Joey** | male  |

---
### Bug Reporting

If you found any bug, create an [issue](https://github.com/TBETool/aws-polly/issues/new).

---
### Support and Contribution

Something is missing? 
* `Fork` the repositroy
* Make your contribution
* make a `pull request`

