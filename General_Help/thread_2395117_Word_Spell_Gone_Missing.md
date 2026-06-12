---
title: "Word Spell Gone Missing"
date: 2018-06-26
forum: General Help
---

### Post by skyesharica on 2018-06-26
Howdy Linux friends,
I am writing a blockbuster book on Linux (Xubuntu 16.04 LTS - I've just upgraded from Xubuntu 14.04 LTS), on LibreOffice Writer.  I have suddenly lost the extremely helpful _spelling_ facility - I am not a super speller and so I'm up the creek - oh no.  :confused:

---

### Post by Xian on 2018-06-27
See if this forum post helps:

[https://ubuntuforums.org/showthread.php?t=2355371](https://ubuntuforums.org/showthread.php?t=2355371)

---

### Post by skyesharica on 2018-06-29
> **Xian said:**
> See if this forum post helps:

[https://ubuntuforums.org/showthread.php?t=2355371](https://ubuntuforums.org/showthread.php?t=2355371)

Thankyou very much.  I've just tried the code.  I almost NEVER do any code - in terror that things will blow up - I'm certainly not a programmer.  I got this in the terminal.:

skye@skye-All-Series:~$ sudo apt-get install libreoffice-l10n-en-gb
[sudo] password for skye: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libllvm5.0
Use 'sudo apt autoremove' to remove it.
Suggested packages:
  hunspell-dictionary-en-gb | myspell-dictionary-en-gb hyphen-en-gb
  libreoffice-grammarcheck-en-gb libreoffice-help-en-gb mythes-en-gb
The following NEW packages will be installed:
  libreoffice-l10n-en-gb
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
Need to get 435 kB of archives.
After this operation, 2,648 kB of additional disk space will be used.
Get:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libreoffice-l10n-en-gb all 1:5.1.4-0ubuntu1 [435 kB]
Fetched 435 kB in 1s (303 kB/s)                 
Selecting previously unselected package libreoffice-l10n-en-gb.
(Reading database ... 201336 files and directories currently installed.)
Preparing to unpack .../libreoffice-l10n-en-gb_1%3a5.1.4-0ubuntu1_all.deb ...
Unpacking libreoffice-l10n-en-gb (1:5.1.4-0ubuntu1) ...
Setting up libreoffice-l10n-en-gb (1:5.1.4-0ubuntu1) ...

Then I opened Language Support and it did say that something had to be installed.  I just have to restart now.  But I'll let you know if it worked.   :KS

FABULOUS - It worked!  I've got my whole book spell checked.  Thanks so much!

---

