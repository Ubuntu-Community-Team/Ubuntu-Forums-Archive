---
title: "Sign the CoC - the GPG command"
date: 2012-12-25
forum: General Help
---

### Post by ibjsb4 on 2012-12-25
> Retrieving the key using the GPG command

Open a terminal and enter:

gpg --fingerprint

GPG will display a message similar to:

pub 1024D/12345678 2007-01-26
Key fingerprint = 0464 39CD 2486 190A 2C5A 0739 0E68 04DC 16E7 CB72
Geoffrey Hayes (My OpenPGP key) <geoffrey@bungle.com>
sub 2048g/ABCDEF12 2007-01-26

Highlight and copy only the numeric fingerprint: 0464 39CD 2486 190A 2C5A 0739 0E68 04DC 16E7 CB72 in the example above. 
> host@host:~$ gpg --fingerprint
gpg: directory `/home/host/.gnupg' created
gpg: new configuration file `/home/host/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/host/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/host/.gnupg/pubring.gpg' created
gpg: /home/host/.gnupg/trustdb.gpg: trustdb created
host@host:~$ gpg --fingerprint
host@host:~$ gpg --fingerprint
host@host:~$And nothing.  Next I see that "app-install-data" may be required.  so ..

> host@host:~$ sudo apt-get install app-install-data
The following NEW packages will be installed:
  app-install-data
0 upgraded, 1 newly installed, 0 to remove and 21 not upgraded.
Need to get 7,177 kB of archives.
After this operation, 10.5 MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main app-install-data all 0.12.04.4 [7,177 kB]
Fetched 7,177 kB in 5s (1,319 kB/s)           
dpkg: warning: files list file for package `adobereader-jpn' missing, assuming package has no files currently installed.
Unpacking app-install-data (from .../app-install-data_0.12.04.4_all.deb) ...
Setting up app-install-data (0.12.04.4) ...
host@host:~$ gpg --fingerprint
host@host:~$ And again nothing.  Now to open "~/.gnupg" it looks like I need to install "kgpg && seahorse-nautilus".  Which I start to do, but get this:

> Additional software has to be installed

Please take a look at the list of changes below.
83.0 MB will be downloaded in total.
[COLOR=Red]275[/COLOR] MB more disk space will be used.So instead I just install "seahorse-nautilus", that was just 10 meg.  And again in terminal "gpg --fingerprint" and still nothing.

All I want to do is sign the CoC, any suggestions?  Also this is a minimum 12o4 install I am working off of, so maybe I missed a needed package.  Any thoughts?

And Merry Christmas  :)

---

### Post by deadflowr on 2012-12-25
I do remember it was really simple and when I finally got it done I felt like an idiot, so don't worry if you feel the same at the end of the process.

Here are two links that might help:

[http://askubuntu.com/questions/100281/how-do-i-make-a-pgp-key]("http://askubuntu.com/questions/100281/how-do-i-make-a-pgp-key")

[http://askubuntu.com/questions/100275/how-do-i-sign-the-ubuntu-code-of-conduct]("http://askubuntu.com/questions/100275/how-do-i-sign-the-ubuntu-code-of-conduct")

---

### Post by ibjsb4 on 2012-12-25
Hi deadflowr

Me thinks I just answered my own question.  I just notice that "password and keys" is now in my main menu.

---

### Post by ibjsb4 on 2012-12-25
Yep, moral of the story:

When not smart enough to use the terminal, use the GUI.  Solved :D

---

