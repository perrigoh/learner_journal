# Virtualenv, Python's venv and Conda environment

Quick reference for managing virtual environment using Virtualenv, Python's venv and Conda environment.  

</br>

|| Virtualenv | venv | Conda |
|---|---|---|---|
| Require installation | &#9989; Need to install Virtualenv | &#10060; No need to install, it is Python's standard package from version 3.3 onwards | &#9989; Need to install Anaconda |
| Create Multiple Python versions | &#9989;  Able to create multiple Python version, but need to install the specific version first | &#10060; Only use system default Python version | &#9989; Able to create multiple Python versions within Conda available package |
| Need to navigate to the current working directory (folder) before running command | &#9989; Need to change the directory (folder) before command | &#9989; Need to change the directory (folder) before command | &#10060; No need to change the directory (folder) in most cases |
| Create a virtual environment and install the package in one command | &#10060; Require activating virtual environment before install package | &#10060; Require activating virtual environment before install package | &#9989; Able to create a virtual environment and install package concurrently, Conda advise better to do so to prevent dependency conflicts |
| Method to install packages | pip | pip | pip and Conda |
|||||

Software environment used to run the examples:  

* Operating system: Windows 11 Home
* Code editor: Visual Studio Code 1.73.0
* Terminal : Git Bash 4.4.23(1)-release run in Visual Studio Code

Note: This topic is done in Dec 2022, information may not be as useful after some time as there will be constant improvement to the environment management tools. To have the most updated information, refer to each environment management tool documentation:

* [Virtualenv documentation](https://virtualenv.pypa.io/en/latest/)
* [venv documentation](https://docs.python.org/3/library/venv.html)
* [Conda manage environments documentation](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)

</br>

## Virtualenv

* Virtualenv creates a virtual environment in any specified directory (folder), hence the virtual environment can be saved alongside the project code directory (folder) for easy reference.  

* It is not part of the Python standard package, installation is required.  

* It can create a virtual environment with a different Python version instead of the system's default, requiring the installation of the other Python version first.  

For more installation information [refer here](https://virtualenv.pypa.io/en/latest/installation.html) and options available [refer here](https://virtualenv.pypa.io/en/latest/cli_interface.html), quick install:  
`python -m pip install virtualenv`  

Youtube tutorial on how to use Virtualenv [refer here](https://youtu.be/N5vscPTWKOk)  

</br>

### Virtualenv creates a virtual environment using the system’s default python version  

Steps:

1. Change the directory to the directory (folder) where the new virtual environment is to be stored:

    ```bash
    $ cd virtual_env/
    ```
    Output:
    ```bash
    NO OUTPUT
    ```

    The prompt will change to from `[wmxpg] ~` to `[wmxpg] ~/virtual_env/`  

2. Create the virtual environment:  
   `virtualenv` is the command, `project_webapp` is the name of the environment

    ```bash
    $ python -m virtualenv project_webapp
    ```
    Output:
    ```bash  
    created virtual environment CPython3.9.13.final.0-64 in 10658ms
    creator Venv(dest=C:\Users\wmxpg\virtual_env\project_webapp, clear=False, no_vcs_ignore=False, global=False, describe=CPython3Windows)
    seeder FromAppData(download=False, pip=bundle, setuptools=bundle, wheel=bundle, via=copy, app_data_dir=C:\Users\wmxpg...\pypa\virtualenv)
    \added seed packages: pip==22.3.1, setuptools==65.5.1, wheel==0.38.4
    activators BashActivator,BatchActivator,FishActivator,NushellActivator,PowerShellActivator,PythonActivator
    ```

    Note: command `virtualenv project_webapp` will not work for this case using Windows system with Git Bash terminal.

</br>

### Virtualenv to install different Python versions

[info source](https://www.freecodecamp.org/news/installing-multiple-python-versions-on-windows-using-virtualenv/)  
Note: Below commands may look different from the info source as it has been customed to work with my system environment.

Steps:

1. Download the specific [Python version for Windows](https://www.python.org/downloads/windows/). Run the installation by clicking on the `python-x.xx-amd64.exe` file. In the installation prompt, jot down the location `C:\Users\wmxpg\AppData\Local\Programs\Python\Pythonxxx` where this programme is to be installed and **do not tick** `Add Python x.x to PATH`.

2. Change the directory to the directory (folder) where the new virtual environment is to be stored:

    ```bash
    $ cd virtual_env/
    ```
    Output:
    ```bash
    NO OUTPUT
    ```

    The prompt will change to from `[wmxpg] ~` to `[wmxpg] ~/virtual_env/`  

3. Create the virtual environment:  
   `virtualenv` is the command, `project_testpyversion` is the name of the environment, `-p`= `--python`, `"C:\...\Pythonxxx\python.exe"` is the path of the Python executable file  

    ```bash
    $ python -m virtualenv project_testpyversion -p 
    ```
    Output:
    ```bash
    "C:\Users\wmxpg\AppData\Local\Programs\Python\Python311\python.exe"
    created virtual environment CPython3.11.0.final.0-64 in 6214ms
    creator CPython3Windows(dest=C:\Users\wmxpg\virtual_env\project_testpyversion, clear=False, no_vcs_ignore=False, global=False)
    seeder FromAppData(download=False, pip=bundle, setuptools=bundle, wheel=bundle, via=copy, app_data_dir=C:\Users\wmxpg\AppData\Local\Packages\PythonSoftwareFoundation.Python
    .3.9_qbz5n2kfra8p0\LocalCache\Local\pypa\virtualenv)
    added seed packages: pip==22.1.2, setuptools==62.6.0, wheel==0.37.1
    activators BashActivator,BatchActivator,FishActivator,NushellActivator,PowerShellActivator,PythonActivator
    ```

    Note: command `virtualenv project_testpyversion` will not work for this case using Windows system with Git Bash terminal.  

</br>

### Activate virtualenv environment

Steps:

1. Change the directory to the created virtual environment folder:

    ```bash
    $ cd virtual_env/project_webapp/
    ```
    Output:
    ```bash
    NO OUTPUT
    ```

    The prompt will change to from `[wmxpg] ~` to `[wmxpg] ~/virtual_env/project_webapp`  

2. Check the 'Scripts' folder is inside the virtual environment folder:

    ```bash
    $ ls
    ```
    Output:
    ```bash
    Include/  Lib/  pyvenv.cfg  Scripts/
    ```

3. Activate the virtual environment:

    ```bash
    $ . Scripts/activate
    # or
    $ source Scripts/activate
    ```
    Output:
    ```bash
    (project_webapp)
    [wmxpg] ~/virtual_env/project_webapp
    ```

    The name of the virtual environment within the parentheses will appear above the prompt.
    Note: command `source project_webapp/bin/activate` will not work for this case using Windows system with Git Bash terminal.  

</br>

### Check which virtual environment currently in

Activate the virtual environment first, then run the command:

```bash
$ which python
```
Output:
```bash
/c/Users/wmxpg/virtual_env/project_webapp/Scripts/python
```

The same method can be applied to any other package `which package_name`.

</br>

### pip install packages and export requirements.txt for virtualenv

As pip commands are the same for Virtualenv, venv and Conda virtual environment, refer below section - [Using pip to install packages and export requirements.txt](#using-pip-to-install-packages-into-virtual-environment-and-export-requirements.txt) for quick reference.

</br>

### Create a virtualenv virtual environment using system site-packages

Steps:

1. Change the directory to the directory (folder) where the new virtual environment is to be stored:

    ```bash
    $ cd virtual_env/
    ```
    Output:
    ```bash
    NO OUTPUT
    ```

    The prompt will change to from `[wmxpg] ~` to `[wmxpg] ~/virtual_env/`  

2. Create the virtual environment:  
   `virtualenv` is the command, `test_virtualenv_syspackage` is the name of the environment  

    ```bash
    $ python -m virtualenv test_virtualenv_syspackage --system-site-packages  
    ```
    Output:
    ```bash
    created virtual environment CPython3.9.13.final.0-64 in 2437ms
    ...
       activators BashActivator,BatchActivator,FishActivator,NushellActivator,PowerShellActivator,PythonActivator
    ```

    Note: command `virtualenv test_virtualenv_syspackage` will not work for this case using Windows system with Git Bash terminal.  

3. To check the environment has been created:

    ```bash
    $ ls
    ```
    Output:
    ```bash
    project_testpyversion/  project_webapp/  test_virtualenv_syspackage/
    ```

    The new environment `test_virtualenv_syspackage` will be created and saved in the current working directory (folder).

4. Activate the virtual environment:

    ```bash
    $ . test_virtualenv_syspackage/Scripts/activate
    # or
    $ source test_venv_syspackage/Scripts/activate
    ```
    Output:
    ```bash
    (test_virtualenv_syspackage)
    [wmxpg] ~/virtual_env/test_virtualenv_syspackage
    ```  

    The name of the virtual environment within the parentheses will appear above the prompt.
    Note: command `source test_virtualenv_syspackage/bin/activate` will not work for this case using Windows system with Git Bash terminal.  

5. To check the list of packages installed in the virtual environment:

    ```bash
    $ pip list
    ```
    Output:
    ```bash
    Package                           Version
    --------------------------------- -----------
    analytics-python                  1.4.0
    anyio                             3.6.1
    argon2-cffi                       21.3.0
    ...
    XlsxWriter                        3.0.2
    zipp                              3.8.0
    ```

    The list will show the entire global packages.  

6. To check the list of packages in the local virtual environment:

    ```bash
    $ pip list --local
    ```
    Output:
    ```bash
    Package    Version
    ---------- -------
    pip        22.0.4
    setuptools 58.1.0
    ```

    The list will show the local packages in this environment.

</br>

### Deactivate the Virtualenv environment

```bash
$ deactivate
```
Output:
```bash
NO OUTPUT
```

Once deactivated, the `(testvirtualenv)` will disappear.  

</br>

### Remove/delete the Virtualenv created virtual environment

Before running the command, deactivate the virtual environment and ensure that the terminal prompt is at the parent directory (folder) of the virtual environment that is going to be deleted.  
`rm` stands for remove, `-r` stands for recursively delete a directory and all its contents, `testvirtualenv` is the folder name of the virtual environment:  

```bash
$ rm -r testvirtualenv
```
Output:
```bash
NO OUTPUT
```

The virtual environment will be deleted, run the command `ls` to check.

</br>

## Python's venv

* venv creates virtual environment in any specified directory (folder), hence the virtual environment can be saved alongside the project code directory (folder) for easy reference.  

* It is a standard package in Python version 3.3 onwards, **no installation** required. For older Python versions, use [Virtualenv](#virtualenv).  

* It creates virtual environment with the system's default Python version only. For multiple Python version environment use either [Virtualenv](#virtualenv) or [Conda](#conda-environment)  

Quick reference on the command to use venv [refer here](https://docs.python.org/3/tutorial/venv.html)  

Youtube tutorial on how to use venv [refer here](https://youtu.be/Kg1Yvry_Ydk)  

</br>

### venv creates virtual environment

Steps:

1. Change the directory to the directory (folder) where the new virtual environment is to be stored:

    ```bash
    $ cd virtual_env/
    ```
    Output:
    ```bash
    NO OUTPUT
    ```

    The prompt will change to from `[wmxpg] ~` to `[wmxpg] ~/virtual_env/`  

2. Create the virtual environment:  
   `venv` is the command, `test_venv` is the name of the environment  

    ```bash
    $ python -m venv test_venv  
    ```
    Output:
    ```bash
    NO OUTPUT
    ```

    Note: command `venv test_venv` will not work for this case using Windows system with Git Bash terminal.  

3. To check the environment has been created:

    ```bash
    $ ls
    ```
    Output:
    ```bash
    project_testpyversion/  project_webapp/  test_venv/
    ```

    The new environment `test_venv` will be created and saved in the current working directory (folder).

</br>

### Activate venv environment

Steps:

1. This method goes straight to activate the environment, instead of checking the `Scripts` folder inside the virtual environment folder:

    ```bash
    $ . test_venv/Scripts/activate
    # or
    $ source test_venv/Scripts/activate
    ```
    Output:
    ```bash    
    (test_venv)
    [wmxpg] ~/virtual_env/test_venv
    ```

    The name of the virtual environment within the parentheses will appear above the prompt.
    Note: command `source test_venv/bin/activate` will not work for this case using Windows system with Git Bash terminal.  

2. To check whether in the correct virtual environment:

    ```bash
    $ where python
    ```
    Output:
    ```bash
    C:\Users\wmxpg\virtual_env\test_venv\Scripts\python.exe
    C:\Users\wmxpg\AppData\Local\Microsoft\WindowsApps\python.exe
    C:\Users\wmxpg\anaconda3\python.exe
    ```

    The first path `C:\Users\wmxpg\virtual_env\test_venv\Scripts\python.exe` is the current working environment.

    or  

    ```bash
    $ which python
    ```
    Output:
    ```bash
    /c/Users/wmxpg/virtual_env/\Users\wmxpg\virtual_env\test_venv/Scripts/python
    ```

</br>

### pip install packages and export requirements.txt for venv  

As pip commands are the same for Virtualenv, venv and conda virtual environment, refer below section - [Using pip to install packages and export requirements.txt](#using-pip-to-install-packages-into-virtual-environment-and-export-requirements.txt) for quick reference.

### Create a venv virtual environment using system site-packages

Steps:

1. Change the directory to the directory (folder) where the new virtual environment is to be stored:

    ```bash
    $ cd virtual_env/
    ```
    Output:
    ```bash
    NO OUTPUT
    ```

    The prompt will change to from `[wmxpg] ~` to `[wmxpg] ~/virtual_env/`  

2. Create the virtual environment:  
   `venv` is the command, `test_venv_syspackage` is the name of the environment

    ```bash
    $ python -m venv test_venv_syspackage --system-site-packages  
    ```
    Output:
    ```bash
    NO OUTPUT
    ```

    Note: command `venv test_venv_syspackage` will not work for this case using Windows system with Git Bash terminal.  

3. To check the environment has been created:

    ```bash
    $ ls
    ```
    Output:
    ```bash
    project_testpyversion/  project_webapp/  test_venv_syspackage/
    ```

    The new environment `test_venv_syspackage` will be created and saved in the current working directory (folder).

4. Activate the virtual environment:

    ```bash
    $ . test_venv_syspackage/Scripts/activate
    # or
    $ source test_venv_syspackage/Scripts/activate
    ```
    Output:
    ```bash
    (test_venv_syspackage)
    [wmxpg] ~/virtual_env/test_venv_syspackage
    ```  

    The name of the virtual environment within the parentheses will appear above the prompt.
    Note: command `source test_venv_syspackage/bin/activate` will not work for this case using Windows system with Git Bash terminal.  

5. To check the list of packages installed in the virtual environment:

    ```bash
    $ pip list
    ```
    Output:
    ```bash
    Package                           Version
    --------------------------------- -----------
    analytics-python                  1.4.0
    anyio                             3.6.1
    argon2-cffi                       21.3.0
    ...
    XlsxWriter                        3.0.2
    zipp                              3.8.0
    ```

    The entire global package will show in the list.

6. To check the list of packages in the local virtual environment:

    ```bash
    $ pip list --local
    ```
    Output:
    ```bash
    Package    Version
    ---------- -------
    pip        22.0.4
    setuptools 58.1.0
    ```

    The list will show the local packages in this environment.

</br>

### Deactivate the venv environment

```bash
$ deactivate
```
Output:
```bash
NO OUTPUT
```

Once deactivated, the `(test_venv)` will disappear.  

</br>

### Remove/delete the venv created virtual environment

Before running the command, deactivate the virtual environment and ensure that the terminal prompt is at the parent directory (folder) of the virtual environment that is going to be deleted.  
`rm` stands for remove, `-r` stands for recursively delete a directory and all its contents, `test_venv` is the folder name of the virtual environment:  

```bash
$ rm -r test_venv
```
Output:
```bash
NO OUTPUT
```

The virtual environment will be deleted, run the command `ls` to check.

</br>

## Using pip to install packages into virtual environment and export requirements.txt

The pip commands for Virtualenv, venv and conda virtual environment are the same. For full pip commands refer to the [pip documentation](https://pip.pypa.io/en/stable/cli/).  

Activate the virtual environment first:

* To activate the Virtualenv environment [refer here](#activate-virtualenv-environment)
* To activate the venv environment [refer here](#activate-venv-environment)
* To activate the Conda environment refer to [Create a Conda environment in the Conda default directory (folder)](#create-a-conda-environment-in-the-conda-default-directory-(folder)) - To activate the Conda environment  

### pip to list the installed packages

```bash
$ pip list
# or
$ python -m pip list
```
Output:
```bash
Package    Version
---------- -------
pip        22.3.1
setuptools 65.5.1
wheel      0.38.4
```

</br>

### pip install package into the virtual environment

Steps:

1. Install the package using pip and activate the virtual environment first:  

    ```bash
    $ pip install numpy
    # or
    $ python -m pip install numpy
    ```
    Output:
    ```bash
    Collecting numpy
    Downloading numpy-1.23.5-cp39-cp39-win_amd64.whl (14.7 MB)
    ...
    Successfully installed numpy-1.23.5
    ```

2. List the installed package in this environment:

    ```bash
    $ pip list
    ```
    Output:
    ```bash
    Package    Version
    ---------- -------
    numpy      1.23.5
    pip        22.3.1
    setuptools 65.5.1
    wheel      0.38.4
    ```

</br>

### Export packages to use in another project

Use `pip freeze -l` or `pip freeze --local` for exporting only local installed packages and `pip freeze --all` to include setuptools, distribute, wheel and pip.

[Refer here](https://pip.pypa.io/en/stable/cli/pip_freeze/) for all options available and examples.  

```bash
$ pip freeze > requirements.txt
# or 
$ python -m  pip freeze > requirements.txt
```
Output:
```bash
NO OUTPUT
```

The requirements.txt file will be created and saved in the current working directory (folder).

</br>

### Read and output content of the requirements.txt created

```bash
$ cat requirements.txt
```
Output:
```bash
numpy==1.23.5
```

</br>

### To install the packages from requirements.txt

Steps:

1. Change the directory to the directory (folder) where the requirements.txt file is stored, in this example the file is stored in the project_webapp directory (folder):

    ```bash
    $ cd virtual_env/project_webapp/
    ```
    Output:
    ```bash
    NO OUTPUT
    ```

    The prompt will change to from `[wmxpg] ~` to `[wmxpg] ~/virtual_env/project_webapp`  

2. Install the requirements.  
   `-r`= `--requirement`:

    ```bash
    $ pip install -r requirements.txt
    ```
    Output:
    ```bash
    Collecting numpy==1.23.5
    Downloading numpy-1.23.5-cp311-cp311-win_amd64.whl (14.6 MB)
    ...
    Successfully installed numpy-1.23.5
    ```

3. Check the package has been installed:

    ```bash
    $ pip list
    ```
    Output:
    ```bash
    Package    Version
    ---------- -------
    numpy      1.23.5
    pip        22.1.2
    setuptools 62.6.0
    wheel      0.37.1
    ```

</br>

## Conda environment

* Conda allows the creation of a virtual environment in both the default directory (folder) `c:\xxx\xxx\anaconda3\envs` and the specified directory (folder). In addition, the virtual environment can be created using an environment.yml file [refer here](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#creating-an-environment-from-an-environment-yml-file) for the command.

* It can create a virtual environment with a different Python version and no preinstallation of different a Python version is needed.  
Note: Though the [web documentation](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-python.html) stated the default Python version is 3.9, the actual Python version installed is 3.10.8 when a virtual environment was created on 9 Dec 2022.  

Quick reference on the command to use Conda environment [refer here](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)  

Youtube tutorial on how to use venv [refer here](https://youtu.be/1VVCd0eSkYc)  

</br>

### Check Conda's available Python versions

To check the python versions available for installation [info source](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-python.html#viewing-a-list-of-available-python-versions):  

```bash
$ conda search python
```
Output:
```bash
Loading channels: done
# Name                       Version           Build  Channel
python                        2.7.13     h1b6d89f_16  pkgs/main
python                        2.7.13     h9912b81_15  pkgs/main
...
python                        3.10.8      h966fe2a_1  pkgs/main
python                        3.10.8      hbb2ffb3_0  pkgs/main
```

</br>

### Create a Conda environment in the Conda default directory (folder)

Note: When creating a virtual environment without specifying Python, the virtual environment created will not have any Python installed. [info source - remarks under steps 2.](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#creating-an-environment-with-commands).

Create virtual environment with Python:  
`-n` = `--name` both can be used interchangeably testcondaenv` is the environment name, `python` install the Conda latest available Python version which is Python version 3.10.8.  _This test example was done on 9 Dec 2022, the default Python version may change._

```bash
$ conda create --name testcondaenv python
```
Output:
```bash
Collecting package metadata (current_repodata.json): done
...
Proceed ([y]/n)? y
...
Retrieving notices: ...working... done
```

When need to use a specific Python version, use the command python=version e.g. `python=3.9`. To check the list of Conda available Python versions [refer here](#check-conda-available-python-version).  

To activate the Conda environment:  

```bash
$ conda activate testcondaenv
(testcondaenv)
[wmxpg] ~/vitrual_env/project_webapp/testcondaenv
```  

The name of the virtual environment within the parentheses will appear above the prompt.  

</br>

### Create a Conda environment in a specific directory (folder)

Steps:

1. Change the directory to the directory (folder) where the new virtual environment is to be stored:  

    ```bash
    $ cd project_datascience/
    ```
    Output:
    ```bash
    NO OUTPUT
    ```

    The prompt will change to from `[wmxpg] ~` to `[wmxpg] ~/project_datascience/`  

2. Create the virtual environment in a specified directory (folder):  
    `testcondadiffdir` is the environment name, `python=3.9` this example specific the Python version to be installed:  

    ```bash
    $ conda create --prefix ./testcondadiffdir python=3.9
    ```
    Output:
    ```bash
    Collecting package metadata (current_repodata.json): done
    Solving environment: done
    ...
    Proceed ([y]/n)? y
    ...
    Retrieving notices: ...working... done
    ```

3. To check the new environment has been created:  

    ```bash
    $ conda env list
    # or
    $ conda info --envs
    ```
    Output:
    ```bash
    # conda environments:
    #
    base                     C:\Users\wmxpg\anaconda3
    deep-learning            C:\Users\wmxpg\anaconda3\envs\deep-learning
    testcondaenv             C:\Users\wmxpg\anaconda3\envs\testcondaenv
                             C:\Users\wmxpg\project_datascience\testcondadiffdir
    ```

    The new virtual environment `C:\Users\wmxpg\project_datascience\testcondadiffdir` has been created.  

4. To activate the environment, the current working directory (folder) needs to be at the directory (folder) where the environment is in `[wmxpg] ~/project_datascience`:

    ```bash
    $ conda activate ./testcondadiffdir
    ```
    Output:
    ```bash
    (C:\Users~/project_datasciencewmxpg\project_datascience02:30:33estcondadiffdir)
    [wmxpg] ~/project_datascience
    ```

    A path-like string within the parentheses will appear above the prompt.  

</br>

### Conda command to check the current working virtual environment  

Activate the virtual environment first, then run the command:

```bash
$ conda env list
# or
$ conda info --envs
```
Output:
```
# conda environments:
#
base                     C:\Users\wmxpg\anaconda3
deep-learning            C:\Users\wmxpg\anaconda3\envs\deep-learning
testcondaenv          *  C:\Users\wmxpg\anaconda3\envs\testcondaenv
                         C:\Users\wmxpg\project_datascience\testcondadiffdir
```

The current virtual environment is marked with an asterisk `*`.  

</br>

### Conda install packages

Installation of packages can be done with either the Conda command or the pip command. This section use Conda install command [refer here](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-pkgs.html#installing-packages) for more details.  

If the preference is to use the pip install command refer to the above section - [Using pip to install packages and export requirements.txt](#using-pip-to-install-packages-into-virtual-environment-and-export-requirements.txt).

**Install the package in the activated environment:**  
`numpy` is the name of the package

```bash
$ conda install numpy 
```
Output:
```bash
Collecting package metadata (current_repodata.json): done
Solving environment: done
...
The following NEW packages will be INSTALLED:

  blas               pkgs/main/win-64::blas-1.0-mkl None
  intel-openmp       pkgs/main/win-64::intel-openmp-2021.4.0-haa95532_3556 None
  mkl                pkgs/main/win-64::mkl-2021.4.0-haa95532_640 None
  mkl-service        pkgs/main/win-64::mkl-service-2.4.0-py310h2bbff1b_0 None
  mkl_fft            pkgs/main/win-64::mkl_fft-1.3.1-py310ha0764ea_0 None
  mkl_random         pkgs/main/win-64::mkl_random-1.2.2-py310h4ed8f06_0 None
  numpy              pkgs/main/win-64::numpy-1.23.4-py310h60c9a35_0 None
  numpy-base         pkgs/main/win-64::numpy-base-1.23.4-py310h04254f7_0 None
  six                pkgs/main/noarch::six-1.16.0-pyhd3eb1b0_1 None

Proceed ([y]/n)? y
...
Retrieving notices: ...working... done
```

Conda will install the specified package and all the dependencies of the package. When need to use a specific package version, use the command packagename=version e.g. `numpy=1.22`. For the list of Conda available package versions, run the command `conda search packagename`. Additional packages can be installed together by adding a space followed by the package name e.g. `conda install numpy matplotlib`.  

**Install package to a specific Conda environment without activating the environment:**  
`-n` = `--name` both can be used interchangeably, `testcondaenv` is the name of the virtual environment, `numpy=1.22` is the name and version of the package

```bash
$ conda install --name testcondaenv numpy=1.22
```
Output:
```bash
Collecting package metadata (current_repodata.json): done
...
The following NEW packages will be INSTALLED:

  blas               pkgs/main/win-64::blas-1.0-mkl None
  intel-openmp       pkgs/main/win-64::intel-openmp-2021.4.0-haa95532_3556 None
  mkl                pkgs/main/win-64::mkl-2021.4.0-haa95532_640 None
  mkl-service        pkgs/main/win-64::mkl-service-2.4.0-py310h2bbff1b_0 None
  mkl_fft            pkgs/main/win-64::mkl_fft-1.3.1-py310ha0764ea_0 None
  mkl_random         pkgs/main/win-64::mkl_random-1.2.2-py310h4ed8f06_0 None
  numpy              pkgs/main/win-64::numpy-1.22.3-py310h6d2d95c_0 None
  numpy-base         pkgs/main/win-64::numpy-base-1.22.3-py310h206c741_0 None
  six                pkgs/main/noarch::six-1.16.0-pyhd3eb1b0_1 None

Proceed ([y]/n)? y
...
Executing transaction: done
Retrieving notices: ...working... done
```

NumPy version 1.22.3 has been installed instead of the latest Conda available version.  

</br>

### Conda to list packages installed in the environment

**List packages in the activated environment:**  

```bash
$ conda list
```
Output:
```bash
# packages in environment at C:\Users\wmxpg\anaconda3\envs\testcondaenv:
#
# Name                    Version                   Build  Channel
blas                      1.0                         mkl  
bzip2                     1.0.8                he774522_0  
ca-certificates           2022.10.11           haa95532_0  
...
xz                        5.2.8                h8cc25b3_0
zlib                      1.2.13               h8cc25b3_0
```

**List package by specifying Conda environment without activating the environment:**  
`-n` = `--name` both can be used interchangeably, `testcondaenv` is the name of the virtual environment

```bash
$ conda list -n testcondaenv
```
Output:
```bash
# packages in environment at C:\Users\wmxpg\anaconda3\envs\testcondaenv:
#
# Name                    Version                   Build  Channel
blas                      1.0                         mkl
bzip2                     1.0.8                he774522_0
ca-certificates           2022.10.11           haa95532_0
...
xz                        5.2.8                h8cc25b3_0
zlib                      1.2.13               h8cc25b3_0
```  

</br>

### Conda to export the list of installed packages

**Export list of packages in the activated environment:**  
`testcondaenv_packages` is the file name

```bash
$ conda list --export > testcondaenv_packages.txt
```
Output:
```bash
NO OUTPUT
```

A `testcondaenv_package.txt` file is created in the current working directory (folder).  

**Export list of packages by specifying Conda environment without activating the environment:**  
`-n` = `--name` both can be used interchangeably, `testcondaenv` is the name of the virtual environment, `testcondaenv_packages is the file name

```bash
$ conda list -n testcondaenv --export > testcondaenv_package.txt
```
Output:
```bash
NO OUTPUT
```

A `testcondaenv_package.txt` file is created in the current working directory (folder).  

Note: This exported file is different from requirements.txt, it can only be used to reinstall packages for the Conda environment.  
Example of the file Content:  
> \# This file may be used to create an environment using:  
\# $ conda create --name <env> --file <this file>  
\# platform: win-64  
bzip2=1.0.8=he774522_0  
ca-certificates=2022.10.11=haa95532_0  
certifi=2022.9.24=py310haa95532_0  
libffi=3.4.2=hd77b12b_6  
openssl=1.1.1s=h2bbff1b_0  
pip=22.3.1=py310haa95532_0  
python=3.10.8=h966fe2a_1  
setuptools=65.5.0=py310haa95532_0  
sqlite=3.40.0=h2bbff1b_0  
tk=8.6.12=h2bbff1b_0  
tzdata=2022g=h04d1e81_0  
vc=14.2=h21ff451_1  
vs2015_runtime=14.27.29016=h5e58377_2  
wheel=0.37.1=pyhd3eb1b0_0  
wincertstore=0.2=py310haa95532_2  
xz=5.2.8=h8cc25b3_0  
zlib=1.2.13=h8cc25b3_0  

</br>

### Conda reinstall packages from an exported file  

Steps:

1. Change the directory to the directory (folder) where the `testcondaenv_package.txt`.txt file is stored, in this example the file is stored in the project_webapp directory (folder):

    ```bash
    $ cd anaconda3/envs/testcondaenv
    ```
    Output:
    ```bash
    NO OUTPUT
    ```

    The prompt will change from `[wmxpg] ~` to `[wmxpg] ~/anaconda3/envs/testcondaenv`

2. Install packages from an exported file to a new virtual environment:
`-n` = `--name` both can be used interchangeably, `newcondaenv` is the name of the virtual environment, `testcondaenv_package.txt` is the exported file name

    ```bash
    $ conda create -n newcondaenv --file testcondaenv_package.txt
    ```
    Output:
    ```bash
    Collecting package metadata (current_repodata.json): done
    ...
    environment location: C:\Users\wmxpg\anaconda3\envs\newcondaenv

    added / updated specs:
        - bzip2==1.0.8=he774522_0
        - ca-certificates==2022.10.11=haa95532_0
        - certifi==2022.9.24=py310haa95532_0
        - libffi==3.4.2=hd77b12b_6
        - openssl==1.1.1s=h2bbff1b_0
        - pip==22.3.1=py310haa95532_0
        - python==3.10.8=h966fe2a_1
        - setuptools==65.5.0=py310haa95532_0
        - sqlite==3.40.0=h2bbff1b_0
        - tk==8.6.12=h2bbff1b_0
        - tzdata==2022g=h04d1e81_0
        - vc==14.2=h21ff451_1
        - vs2015_runtime==14.27.29016=h5e58377_2
        - wheel==0.37.1=pyhd3eb1b0_0
        - wincertstore==0.2=py310haa95532_2
        - xz==5.2.8=h8cc25b3_0
        - zlib==1.2.13=h8cc25b3_0
    ...
    Proceed ([y]/n)? y
    ...
    Retrieving notices: ...working... done
    ```  

### Conda remove the installed package

**Remove the installed package in the activated environment:**  

```bash
$ conda remove numpy
```
Output:
```bash
Collecting package metadata (repodata.json): done
Solving environment: done
...
The following packages will be REMOVED:

  blas-1.0-mkl
  intel-openmp-2021.4.0-haa95532_3556
  mkl-2021.4.0-haa95532_640
  mkl-service-2.4.0-py310h2bbff1b_0
  mkl_fft-1.3.1-py310ha0764ea_0
  mkl_random-1.2.2-py310h4ed8f06_0
  numpy-1.23.4-py310h60c9a35_0
  numpy-base-1.23.4-py310h04254f7_0
  six-1.16.0-pyhd3eb1b0_1

Proceed ([y]/n)? y
...
Executing transaction: done
```

Conda will remove the specified package and all the dependencies of the package.  

**Remove the installed package of a specific Conda environment without activating the environment:**  
`-n` = `--name` both can be used interchangeably, `testcondaenv` is the name of the virtual environment  

```bash
$ conda remove -n testcondaenv numpy
```
Output:
```bash
Collecting package metadata (repodata.json): done
...
The following packages will be REMOVED:

  blas-1.0-mkl
  intel-openmp-2021.4.0-haa95532_3556
  mkl-2021.4.0-haa95532_640
  mkl-service-2.4.0-py310h2bbff1b_0
  mkl_fft-1.3.1-py310ha0764ea_0
  mkl_random-1.2.2-py310h4ed8f06_0
  numpy-1.22.3-py310h6d2d95c_0
  numpy-base-1.22.3-py310h206c741_0
  six-1.16.0-pyhd3eb1b0_1

Proceed ([y]/n)? y
...
Executing transaction: done
```  

Conda will remove the specified package and all the dependencies of the package.  

### Deactivate the Conda environment

```bash
$ conda deactivate
```
Output:
```bash
NO OUTPUT
```

Once deactivated, the `(testcondaenv)` will disappear.  

</br>

### Remove/delete the Conda created virtual environment

Before running the command, deactivate the virtual environment:

```bash
$ conda remove --name testcondaenv --all
```
Output:
```bash
Remove all packages in environment C:\Users\wmxpg\anaconda3\envs\testcondaenv:
...
Proceed ([y]/n)? y
...
Executing transaction: done
```

To check the virtual environment has been deleted, run the command `conda env list`.  

## Error encountered

</br>

### Conda environment not able to conda activate  

Error message  
CommandNotFoundError: Your shell has not been properly configured to use 'conda activate'.  

This might happen after the computer had been shut down or restarted. Though, running the command to list the Conda environments is working:

```bash

$ conda env list
```
Output:
```bash
# conda environments:
#
base                     C:\Users\wmxpg\anaconda3
deep-learning            C:\Users\wmxpg\anaconda3\envs\deep-learning
empty_env                C:\Users\wmxpg\anaconda3\envs\empty_env
testcondaenv             C:\Users\wmxpg\anaconda3\envs\testcondaenv
                         C:\Users\wmxpg\project_datascience\testcondadiffdir
```

but not able to activate the environment:

```bash
$ conda activate testcondaenv
```
Output:
```bash
CommandNotFoundError: Your shell has not been properly configured to use 'conda activate'.
If using 'conda activate' from a batch script, change your
invocation to 'CALL conda.bat activate'.

To initialize your shell, run

    $ conda init <SHELL_NAME>

Currently supported shells are:
  - bash
  - cmd.exe
  - fish
  - tcsh
  - xonsh
  - zsh
  - powershell

See 'conda init --help' for more information and options.

IMPORTANT: You may need to close and restart your shell after running 'conda init'.
```  

Run the Conda init command, specifying which shell:
`bash` is the shell used

```bash
$ conda init bash
```
Output:
```bash
no change     C:\Users\wmxpg\anaconda3\Scripts\conda.exe
no change     C:\Users\wmxpg\anaconda3\Scripts\conda-env.exe
no change     C:\Users\wmxpg\anaconda3\Scripts\conda-script.py
...
modified      C:\Users\wmxpg\anaconda3\etc\profile.d\conda.csh
modified      C:\Users\wmxpg\.bash_profile

==> For changes to take effect, close and re-open your current shell. <==
```

There will be a `(base)` above the prompt after the closure and reopen the shell, this means the `base` environment has been activated. Deactivate the `base` environment using `conda deactivate`. Now the terminal is ready to activate any virtual environment using the Conda command.  

</br>

## Reference

Additional information.

</br>

### Speed comparison on creating a virtual environment with Virtualenv, venv and Conda  

Speed of creating virtual environment comparison table:

|| Virtualenv | venv | Conda |
|---|---|---|---|
| Speed: ||||
| Command | $ time python3 -m virtualenv testvirtualenv | $ time python3 -m venv testvenv | $ time conda create -n testcondaenv python=3.9 |
| real | 0m7.319s | 1m26.321s | 0m47.486s |
| user | 0m0.000s | 0m0.015s | 0m0.015s |
| sys |0m0.046s | 0m0.062s | 0m0.030s |
|||||
| Folder size on disk: | 13.7mb | 19.1mb | 126mb |

Virtualenv is faster but not conclusive as the number of files copied into the folder is lesser, resulting in a smaller folder size than the others.  

</br>

### Other learning resources

* [Udacity - AI Programming/Part 2/Lesson 7/ 23. Virtual Environments](https://classroom.udacity.com/nanodegrees/nd089/parts/cd0184/modules/172bc12e-2000-484d-8095-33899ed05418/lessons/3689c9eb-3430-4747-a65e-5c83893d86b1/concepts/1a2681fd-5cd8-4630-ae17-fe5e133f94f5)  
This is a brief introduction to Conda and venv.  
