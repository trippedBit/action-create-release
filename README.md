# action-create-release
Action to create releases when pushing tags.
<br><br>
## License
Please see [LICENSE](LICENSE).
<br><br>
## Usage
Create a workflow file inside your repo in .github/workflow and add the following.
Change the name and the triggering event to fit your needs.
```yml
name: create-release

on:
    push:
        tags:
            - "v*"

jobs:
    create_release:
        runs-on: ubuntu-latest
        steps:
            - uses: trippedBit/action-create-release@v1.0.0
              with:
                secret-input: ${{ secrets.GITHUB_TOKEN }}
                zip-filelist: "dummy_file README.md requirements.txt tests/test_unit.py"
  
```
### Inputs
The following inputs are available:
* secret-input: Secret to use. This is a required input.
* remove-merges: Option to remove merges from changelog. This is an optional input, defaults to "false".
* zip-options: Options for the zip command used in step build_artifacts. This is an optional input, defaults to "" (empty string).
* zip-filelist: List of files to zip. This is an optional input, defaults to "*" (all files in current directory).
