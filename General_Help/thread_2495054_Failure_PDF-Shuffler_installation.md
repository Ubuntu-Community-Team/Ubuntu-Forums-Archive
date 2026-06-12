---
title: "Failure PDF-Shuffler installation"
date: 2024-02-06
forum: General Help
---

### Post by John_Rose on 2024-02-06
Hello,

Sorry if some of the technical terms below are approximate since I am using the French interface and don't always know the equivalent in the English interface.

I am running Ubuntu 22.04 LTS with gnome 42.9 on an ASUS Vivobook 14 notebook. I am a neophyte concerning system matters including python.

I previously had Ubuntu 18.04 LTS with the Gnome Classic interface on another ASUS Vivobook computer and frequently used the application PDF-Shuffler (a very convenient, simple and dependable way to merge and dissociate the pages of pdf files).

I forget how I installed PDF-Shuffler before, but it was a simple procedure found on the web. Now when I try to install it on the new computer I can only find the official page on SourceForge ([https://sourceforge.net/projects/pdfshuffler/](https://sourceforge.net/projects/pdfshuffler/)) which provides a very complex procedure for installation with no user help facility.

From the above site I downloaded pdfshuffler-0.6.0.tar.gz and decompressed to give a pdfshuffler-0.6.0 directory. The README file says:

> PDF-Shuffler requires python-poppler and version 1.10 or newer of python-pypdf.
PDF-Shuffler is written in Python using PyGTK. It is released under the GNU GPL-3.
In order to install run:
 python setup.py install
as superuser.

I didn't have either python-poppler or python-pypdf installed. I do not have python but rather python3. 

I tried to install python-poppler which is supposed to work on Ubuntu 22.04 ([https://cbrunet.net/python-poppler/installation.html](https://cbrunet.net/python-poppler/installation.html)). It says I can install from PyPI or git.

The git method seemed simpler but did not work:
> sudo pip install --use-pep517
[sudo] Mot de passe de john : 
ERROR: You must give at least one requirement to install (see "pip help install")

When I tried the PyPI method (without Python virtual environment since I don't know what this is or how to set it up) I get:

> john@john-asus14:~$ sudo pip install --use-pep517 python-poppler
Collecting python-poppler
  Downloading python_poppler-0.4.1.tar.gz (138 kB)
     &#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473; 138.5/138.5 KB 918.7 kB/s eta 0:00:00
  Installing build dependencies ... done
  Getting requirements to build wheel ... done
  Installing backend dependencies ... done
  Preparing metadata (pyproject.toml) ... error
  error: subprocess-exited-with-error
  
  × Preparing metadata (pyproject.toml) did not run successfully.
  &#9474; exit code: 1
  &#9584;&#9472;> [33 lines of output]
      Traceback (most recent call last):
        File "/usr/lib/python3/dist-packages/pip/_vendor/pep517/in_process/_in_process.py", line 156, in prepare_metadata_for_build_wheel
          hook = backend.prepare_metadata_for_build_wheel
      AttributeError: module 'mesonpy' has no attribute 'prepare_metadata_for_build_wheel'
      
      During handling of the above exception, another exception occurred:
      
      Traceback (most recent call last):
        File "/usr/lib/python3/dist-packages/pip/_vendor/pep517/in_process/_in_process.py", line 363, in <module>
          main()
        File "/usr/lib/python3/dist-packages/pip/_vendor/pep517/in_process/_in_process.py", line 345, in main
          json_out['return_val'] = hook(**hook_input['kwargs'])
        File "/usr/lib/python3/dist-packages/pip/_vendor/pep517/in_process/_in_process.py", line 160, in prepare_metadata_for_build_wheel
          whl_basename = backend.build_wheel(metadata_directory, config_settings)
        File "/tmp/pip-build-env-dkkmclp0/overlay/local/lib/python3.10/dist-packages/mesonpy/__init__.py", line 985, in wrapper
          return func(*args, **kwargs)
        File "/tmp/pip-build-env-dkkmclp0/overlay/local/lib/python3.10/dist-packages/mesonpy/__init__.py", line 1038, in build_wheel
          with _project(config_settings) as project:
        File "/usr/lib/python3.10/contextlib.py", line 135, in __enter__
          return next(self.gen)
        File "/tmp/pip-build-env-dkkmclp0/overlay/local/lib/python3.10/dist-packages/mesonpy/__init__.py", line 912, in _project
          yield Project(source_dir, build_dir, meson_args, editable_verbose)
        File "/tmp/pip-build-env-dkkmclp0/overlay/local/lib/python3.10/dist-packages/mesonpy/__init__.py", line 635, in __init__
          self._meson = _get_meson_command(pyproject_config.get('meson'))
        File "/tmp/pip-build-env-dkkmclp0/overlay/local/lib/python3.10/dist-packages/mesonpy/__init__.py", line 947, in _get_meson_command
          meson_version = subprocess.run(cmd + ['--version'], check=False, text=True, capture_output=True).stdout
        File "/usr/lib/python3.10/subprocess.py", line 503, in run
          with Popen(*popenargs, **kwargs) as process:
        File "/usr/lib/python3.10/subprocess.py", line 971, in __init__
          self._execute_child(args, executable, preexec_fn, close_fds,
        File "/usr/lib/python3.10/subprocess.py", line 1863, in _execute_child
          raise child_exception_type(errno_num, err_msg, err_filename)
      FileNotFoundError: [Errno 2] No such file or directory: 'meson'
      [end of output]
  
  note: This error originates from a subprocess, and is likely not a problem with pip.
error: metadata-generation-failed

× Encountered error while generating package metadata.
&#9584;&#9472;> See above for output.

note: This is an issue with the package mentioned above, not pip.
hint: See above for details.
   
I tried installing python-pypdf which I assume is the same as pypdf 4.0.1 ([https://pypi.org/project/pypdf/](https://pypi.org/project/pypdf/)) and got the following:

> john@john-asus14:~$ pip install pypdf
Defaulting to user installation because normal site-packages is not writeable
Requirement already satisfied: pypdf in ./.local/lib/python3.10/site-packages (3.17.4)
john@john-asus14:~$ sudo pip install pypdf
[sudo] Mot de passe de john : 
Collecting pypdf
  Downloading pypdf-4.0.1-py3-none-any.whl (283 kB)
     &#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473; 284.0/284.0 KB 455.6 kB/s eta 0:00:00
Installing collected packages: pypdf
Successfully installed pypdf-4.0.1
WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager. It is recommended to use a virtual environment instead: [https://pip.pypa.io/warnings/venv](https://pip.pypa.io/warnings/venv)

I now see in Synaptic that I have python3-pypdf2 intalled but do not know whether this is the same as pypdf-4.0.1 or different. Perhaps it was already there and sufficed in which case I should remove pypdf-4.0.1 but how?

I tried nevertheless to install PDF-Shuffler and got the following error:

> john@john-asus14:~$ sudo python3 ~/Téléchargements/pdfshuffler-0.6.0/setup.py install
/home/john/Téléchargements/pdfshuffler-0.6.0/setup.py:26: DeprecationWarning: The distutils package is deprecated and slated for removal in Python 3.12. Use setuptools or check PEP 632 for potential alternatives
  from distutils.core import setup
Traceback (most recent call last):
  File "/home/john/Téléchargements/pdfshuffler-0.6.0/setup.py", line 39, in <module>
    for name in os.listdir('po'):
FileNotFoundError: [Errno 2] No such file or directory: 'po'

I do have PDF-Shuffler in the activities list and the Main Menu (with the correct launch icon) and the launch command pdfshuffler. I don't know whether it was always there are added by the above installation command. But clicking on it yields no action.

All of this is crazy - could someone please help me to correctly install PDF-Shuffler?

Alternatively please inform on a comparable and reliable replacement package (not PDFsam Basic which is unnecessarily complex for me and buggy)?

Thanks and best wishes,
    John

---

### Post by John_Rose on 2024-02-06
Oups, I then saw from the comments on the PDF-Shuffler site (but not in the developer's instructions) that pdfshuffler is now called pdfarranger. I installed it simply from Synaptic Package Manager. It would be nice if someone could propose to the developers to call  their package by the right name!!!

---

### Post by dragonfly41 on 2024-02-06
Thanks for the tip. I am in process of adding apps to fresh Ubuntu 22.04 and this prompted me to install pdfarranger. Useful in concert with pandoc. I will add it as an Albert Python extension. Again I am using Albert as a fulcrum to manage multiple workflows.

---

