## RetDec Regression Tests

A framework for writing and running regression tests for RetDec and related tools.

## Requirements

To run regression tests, you must have:
* Python >= 3.4
* Clang 3.9.1 (exactly this version)
* Cloned our `retdec` repository, built and installed RetDec.
* Cloned our `retdec-regression-tests` repository that contains test cases.

Additionally, to run tests for our IDA plugin, you must have:
* IDA 6.95 (exactly this version; older or newer version are not supported at the moment)
* Cloned our `retdec-idaplugin` repository, built and installed our IDA plugin.

## Installation

* Clone the repository.
* Step inside it:

  ```
  $ cd retdec-regression-tests-framework
  ```

* Install all the needed third-party Python packages, either into a virtual environment:

  ```
  $ python -m venv virtualenv
  $ source virtualenv/bin/activate
  $ pip install -r requirements.txt
  ```

  or into your home directory:

  ```
  $ pip install --user -r requirements.txt
  ```

* Verify that all dependencies have been installed by running

  ```
  python check_dependencies.py
  ```

* Create a new file `config_local.ini` with the following content (you will need to adjust the paths):

  ```
  [runner]
  ; Path to Clang containing subdirectories such as bin, include, lib, share.
  clang_dir = /path/to/clang
  ; Path to the cloned repository containing regression tests.
  tests_root_dir = /path/to/retdec-regression-tests
  ; Path to the RetDec's build directory.
  retdec_build_dir = /path/to/retdec/build
  ; Path to the RetDec's installation directory.
  retdec_installed_dir = /path/to/retdec/installed
  ; Path to the cloned RetDec repository.
  retdec_repo_dir = /path/to/retdec
  ```

* Additionally, if you plan to run tests for our IDA plugin, you have to also include the following settings into the `[runner]` section of the `config_local.ini` file:

  ```
  idaplugin_tests_enabled = 1
  ; Path to the IDA 6.95 directory.
  idaplugin_ida_dir = /path/to/ida
  ; Path to our script run-ida-decompilation from the retdec-idaplugin repository.
  idaplugin_script = /path/to/retdec-idaplugin/scripts/run-ida-decompilation.sh
  ```

## Use

To run all tests, execute

```
$ python runner.py
```

To run only tests in the given directory, execute

```
$ python runner.py path/to/directory
```

For more information, execute

```
$ python runner.py --help
```

## Documentation

To generate detailed documentation on how to write tests, execute

```
$ make docs
```

Then, open `docs/_build/html/index.html` in your favorite web browser.

## License

Copyright (c) 2017 Avast Software, licensed under the MIT license. See the `LICENSE` file for more details.

The framework includes several third-party libraries, whose code and licensing information is provided in the `libs` subdirectory.

## Contributing

See [RetDec contribution guidelines](https://github.com/avast-tl/retdec/wiki/Contribution-Guidelines).
