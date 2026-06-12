---
title: "Deja-Dup not able to connect to Google Drive"
date: 2019-12-14
forum: General Help
---

### Post by kzollman on 2019-12-14
Hello,

I was previously able to use Deja-Dup to backup to my google drive folder in 18.04.  After upgrading to 19.10, I now get this error "Could not log into Google servers. OK" (Picture attached.)  This error comes up immediately, prior to being asked for any account information/passwords/etc.

[ATTACH=CONFIG]284612[/ATTACH]

I am already logged into my Google account via Gnome, and can access my Google drive folder in Nautilus.  

I cannot seem to find any additional error messages to clarify what is the problem.  

Any assistance or thoughts would be much appreciated. 

Thanks!

-kevin

---

### Post by ramirezrubiofx on 2019-12-15
Same problem here

---

### Post by tcpiplab2 on 2019-12-16
I have this problem too:

Ubuntu 19.10
Déjà Dup Backup Tool 40.1

---

### Post by lonelasso on 2019-12-16
Deja-Dup changed the backend to PyDrive from gvfs to talk to Google Drive.
As of today Ubuntu has not packaged pydrive and the package is not in the repository.

[COLOR=#333333][FONT=monospace]To work around this for now, I recommend trying the snap, which does not have this problem:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]snap install deja-dup --classic

or as I did install PyDrive using pip.
sudo pip3 install PyDrive[/FONT][/COLOR]

---

### Post by ramirezrubiofx on 2019-12-17
> **lonelasso said:**
> Deja-Dup changed the backend to PyDrive from gvfs to talk to Google Drive.
As of today Ubuntu has not packaged pydrive and the package is not in the repository.

[COLOR=#333333][FONT=monospace]To work around this for now, I recommend trying the snap, which does not have this problem:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]snap install deja-dup --classic

or as I did install PyDrive using pip.
sudo pip3 install PyDrive[/FONT][/COLOR]

Thank you very much lonelaso!
Is there any advantages in using PyDrive? Absolute ignorant here.:P

---

### Post by kzollman on 2019-12-18
Thanks for the assistance.  

Adding PyDrive was not sufficient.  I continued to receive the same error message.  Is it possible there is something else I also need to install?  (I have a relatively clean install of 19.10.)

Installing the classic version from snap did work, however.  So I'm going with that for now.

---

