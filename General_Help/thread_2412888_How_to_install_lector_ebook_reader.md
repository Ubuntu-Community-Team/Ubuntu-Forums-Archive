---
title: "How to install lector ebook reader"
date: 2019-02-18
forum: General Help
---

### Post by cmcanulty on 2019-02-18
This ebook reader sounds fantastic but how to install it on Ubuntu is a mystery. I saw it in 2 articles and checked out the github page but don't understand what to do. Thank you

[https://www.omgubuntu.co.uk/2018/03/lector-qt-ebook-reader-app-for-kde]("https://www.omgubuntu.co.uk/2018/03/lector-qt-ebook-reader-app-for-kde")

[https://www.ubuntupit.com/lector-open-source-qt-based-ebook-app-ubuntu-linux/]("https://www.ubuntupit.com/lector-open-source-qt-based-ebook-app-ubuntu-linux/")

[https://github.com/BasioMeusPuga/Lector]("https://github.com/BasioMeusPuga/Lector")

---

### Post by Holger_Gehrke on 2019-02-19
Since I'm quite happy with calibre (which mostly covers the same use-cases; for reading comics I'm using something else) I haven't tried to install it. But the instructions seem reasonably clear to me. You need python 3.6 (check what version your python3 is), PyQT5 (package python3-pyqt5), python-lxml (package python3-lxml), python-beautifulsoup4 (package python3-bs4) and python-xmltodict (package python3-xmltodict). Check the versions of the software in the packages against the versions listed on the github-page with 'apt show'. On 18.04 the versions look about right. pymupdf - which is labeled as an optional component - is probably a bit more complicated to install, I couldn't find it in the repos.

If the versions are sufficient the first step is to 'apt install' all the dependencies:
```

sudo apt install python3-pyqt5 python3-lxml python3-bs4 python3-xmltodict
```
Next you need to clone the git-repository:
```

git clone https://github.com/BasioMeusPuga/Lector.git

```
this will create a directory named Lector and download the files into it. Change into that directory.
You can check whether the program works with
```
python3 lector/__main__,py
```
If it does, install it with
```

python3 setup.py build
sudo python3 setup.py install

```
This should install it and put a .desktop-file in some useful location so you should be able to call it from your DE.

---

### Post by #&amp;thj^% on 2019-02-19
It's pretty straight forward;
Requirements Needed **[COLOR="#FF0000"](Install these first):[/COLOR]**
Package Version tested
[list][*]Python 	3.6
[*]PyQt5 	5.10.1
[*]python-lxml 	4.3.0
[*]python-beautifulsoup4 	4.6.0
[*]python-xmltodict 	0.11.0
Optional
Package 	Version tested
[*]python-pymupdf 	1.14.5[/list]

First download the master zip.(See Screenshot)
[list][*]1.Clone repository
[*]2.enter the following in terminal from the directory it was downloaded:
[/list]
```
python setup.py build
sudo python setup.py install
```
Example of how I installed it:
```
cd /home/me/Downloads/Lector-master
python setup.py build
sudo python setup.py install
```
And Result:
```
lector
Locale: en_US (No translations found)
Database: No paths for settings...
Available parsers: *.epub *.mobi *.azw *.azw3 *.azw4 *.prc *.cbz *.cbr *.pdf
Database returned nothing
Saving settings...
57 books found
Finished processing in 5.475958585739136
Saving settings...

```

NOTE:Lector is in a very early development stage, but as Bookworms, you can have a look and taste of this beautiful ebook reader. At this stage, it might be a buggy and missing some critical features.
Ha Ninja'd by Holger_Gehrke ;)

---

### Post by cmcanulty on 2019-02-19
Thanks for the detailed help. In synaptic it doesn't show PyQt5 5.10.1, it does show 5.5.1 and 5.10.1-dev, also doesn't show python-lxml 4.3.0, or python-beautifulsoup4 4.6.0, or python-xmltodict 0.11.0, or python-pymupdf 1.14.5. I do have python 3.6 installed I think because this web page says it comes with Ubuntu 18.04 
[https://www.tecmint.com/install-python-in-ubuntu/]("https://www.tecmint.com/install-python-in-ubuntu/")
so I am lost on how to install all those prerequisites. the rest seems quite understandable

---

### Post by #&amp;thj^% on 2019-02-19
See if these are there:
Depends On :
```
 qt5-base  qt5-multimedia  python  python-pyqt5
python-beautifulsoup4  python-lxml  poppler-qt5
python-poppler-qt5
```

---

### Post by cmcanulty on 2019-02-19
python is there and installed, I installed python-lxml the others aren't listed some similar names but I doubt if that is OK

---

### Post by monkeybrain20122 on 2019-02-19
> **cmcanulty said:**
> Thanks for the detailed help. In synaptic it doesn't show PyQt5 5.10.1, it does show 5.5.1 and 5.10.1-dev, also doesn't show python-lxml 4.3.0, or python-beautifulsoup4 4.6.0, or python-xmltodict 0.11.0, or python-pymupdf 1.14.5. I do have python 3.6 installed I think because this web page says it comes with Ubuntu 18.04 
[https://www.tecmint.com/install-python-in-ubuntu/](https://www.tecmint.com/install-python-in-ubuntu/)
so I am lost on how to install all those prerequisites. the rest seems quite understandable

Which Ubuntu is this?

If repo version is too old (very likely) install PyQt with pip
 ```
sudo pip3 install PyQt5 
```
In general I install all python modules with pip as much as possible. The repo versions are likely very old.

If you have anything before 18.04 then you don't have python3.6, you can either set it up with a virtual environment, anaconda or install python3.6 in a local directory and manipulate the environmental variables when invoke python3.6 (with a script, see my post #5 in this [thread]("https://ubuntuforums.org/showthread.php?t=2410993")) . There are a few ppas for 16.04 which offer python3.6 but they will screw up your system, so don't use any of them.

BTW, how is this better than [calibre]("https://calibre-ebook.com/download_linux")?

---

### Post by #&amp;thj^% on 2019-02-19
Here is all I have installed:
```
awk '$3~/^install$/ {print $4;}' /var/log/dpkg.log
dh-python:all
libqt5xml5:amd64
libpoppler-qt5-1:amd64
libpython3.6-dev:amd64
libpython3-dev:amd64
libqt5designer5:amd64
libqt5sql5:amd64
libqt5help5:amd64
libqt5multimedia5:amd64
libqt5opengl5:amd64
libqt5multimediawidgets5:amd64
libqt5sql5-sqlite:amd64
libqt5test5:amd64
python3-sip:amd64
sip-dev:amd64
python3.6-dev:amd64
python3-dev:amd64
python3-sip-dev:amd64
pyqt5-dev:all
python-beautifulsoup:all
python-pkg-resources:all
python-chardet:all
python-sip:amd64
python-pyqt5:amd64
python-pyqt5.qtmultimedia:amd64
python3-pyqt5:amd64
python3-poppler-qt5:amd64
qtchooser:amd64
qt5-assistant:amd64
qt5-style-plugins:amd64
qt5ct:amd64
mesa-common-dev:amd64
linux-modules-4.15.0-46-generic:amd64
linux-image-4.15.0-46-generic:amd64
linux-modules-extra-4.15.0-46-generic:amd64
linux-headers-4.15.0-46:all
linux-headers-4.15.0-46-generic:amd64
python3-bs4:all
python3-webencodings:all
python3-html5lib:all
python3-lxml:amd64
python3-xmltodict:all
python3-pypdf2:all
python-pypdf2:all
mupdf-tools:amd64
libmupdf-dev:amd64
mupdf:amd64
libpython2.7-dev:amd64
libpython-dev:amd64
libpython-all-dev:amd64
python-all:amd64
python2.7-dev:amd64
python-dev:amd64
python-all-dev:amd64
python-asn1crypto:all
python-cffi-backend:amd64
python-crypto:amd64
python-enum34:all
python-idna:all
python-ipaddress:all
python-six:all
python-cryptography:amd64
python-secretstorage:all
python-keyring:all
python-keyrings.alt:all
python-pip-whl:all
python-pip:all
python-setuptools:all
python-wheel:all
python-xdg:all

```
I then cloned the repo this time via:
```
git clone https://github.com/BasioMeusPuga/Lector.git

```
Then from that Directory:
```
cd Lector
python3 setup.py build
sudo python3 setup.py install

```
The package your having troubles finding is "python-beautifulsoup4 4.6.0" >>is named in ubuntu as"python3-bs4"
from there i launched Lector via:
```
lector
```
While I find it fun to muck about with it as a tester, I suggest waiting for the Developer to package it better for Ubuntu/Debian and add and fix lacking items mentioned in your link.
My Opinion:>>Nothing overwhelming to see here.:)

---

### Post by cmcanulty on 2019-02-19
I am running xubuntu 18.04 with all the latest updates. Whoee that missing python3-bs4 was the ticlrt/ I have it up and running and hopefully will last until they get a good version out. Thanks so much I never would have figured out the missnamed dependency.How did you do that?

---

