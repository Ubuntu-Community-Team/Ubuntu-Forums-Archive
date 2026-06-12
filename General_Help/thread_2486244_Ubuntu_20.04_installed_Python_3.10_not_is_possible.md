---
title: "Ubuntu 20.04 installed Python 3.10 not is possible run python 3.10 softwares"
date: 2023-04-24
forum: General Help
---

### Post by aug7744 on 2023-04-24
Hello.
Thanks for reading my topic.
Ubuntu 20.04 installed python 3.10 from
sudo add-apt-repository ppa:deadsnakes/ppa

When trying install an software requiring python 3.10 is showed message about not having python 3.10 and only the 3.8 version.
Is as if any software can't access or use installed python 3.10 or 3.12.

How fix it ? Have any command or dependencie to install ?

Have an nice day.

---

### Post by bimblesticks on 2023-04-24
PPAs are unsupported, you use them at your own risk. If you want Python 3.10, you should consider upgrading to Jammy Jellyfish (22.04), which on my machine features version 3.10.6.

You can run a specific version of Python by appending the version number to the [FONT=courier new]python[/FONT] command, e.g. [FONT=courier new]python3.10 -V[/FONT] will report the version number. To get help with your software installation issue you'd need to share what software you're trying to install, what method you're using to install it and what the error message actually says.

---

### Post by aug7744 on 2023-04-24
Thanks for your reply.
python3.10 -V show Python 3.10.11

The software is Bible Analyzer
[http://www.bibleanalyzer.com/download.html](http://www.bibleanalyzer.com/download.html)

Download the deb and when using dpkg -i is showed not any Python 3.10 version on OS, but Python 3.10 was installed from

[https://launchpad.net/~deadsnakes/+archive/ubuntu/ppa?field.series_filter=](https://launchpad.net/~deadsnakes/+archive/ubuntu/ppa?field.series_filter=)

---

### Post by Impavidus on 2023-04-25
Some core components of Ubuntu depend on a specific Python version, so if you change the default version of Python, your system will be broken. It is possible to install multiple versions of Python side by side, but the alternative version must be kept isolated from the OS. I've never tried this myself though; although people tell me that Python is a nice language and I've used it on a few occasions, I never liked it, so I don't use it for my personal projects.

The simplest way to get Python 3.10 on Ubuntu is using Ubuntu 22.04. It comes with Python 3.10 by default.

---

### Post by monkeybrain20122 on 2023-04-25
Never install python from ppa because it installs system wide and it will mess with system components which are sensitive to python version. 

If you need a different version of python, always install it locally, e.g use [conda]("https://docs.conda.io/en/latest/").

or [my way]("https://ubuntuforums.org/showthread.php?t=2486174").


P.S so how do you install a .deb that requires a different python version this way? Well if the source code is available you can compile it against the local python and install it locally. Then there is this way that may or may not work depending on the package (I have tried that and it works for some programs): extract the .deb and put the components in the local counterparts in your local environment and invoke it with a script that specifies an alternative $PATH and  $LD_LIBRARY_PATH: for example, put contents of /usr/bin in your deb archive in $PREFIX/bin etc where $PREFIX is where you install the local python. Then you may have to edit some files... This is messy and hacky but often it works.

---

