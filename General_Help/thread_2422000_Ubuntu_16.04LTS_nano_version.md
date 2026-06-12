---
title: "Ubuntu 16.04LTS nano version"
date: 2019-06-30
forum: General Help
---

### Post by Frank P on 2019-06-30
The current version of nano is 4.3. The version in my 16.04 is 2.5.3 Key bindings and options seem quite different when I check the manuals. Can it be updated to 4.3 or is there a better option for making simple changes over ssh. 
Thanks
Frank

---

### Post by uRock on 2019-06-30
I am not seeing a repository that can be added. You can download and install from their website. [https://www.nano-editor.org/download.php](https://www.nano-editor.org/download.php)  I downloaded the nano-4.3.tar.gz file, then right-clicked and extracted it. Check out the README file inside for steps to install. I had to run these commands before being able to get it working. 

```
sudo apt-get remove nano && sudo apt install build-essential libncursesw5-dev groff
```

---

### Post by Frank P on 2019-06-30
I'll download and install that tomorrow
Thanks
Frank

---

### Post by deadflowr on 2019-07-01
What manual are you checking?
nano built for Ubuntu comes with the manual for the version it builds.

---

### Post by Frank P on 2019-07-01
I was reading the Ubuntu nano 2.5.3 help page-  ctrl+g, looking for a copy/paste. Couldn't find it so I went to their page - [FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]https://www.nano-editor.org/docs.php where I noticed there's a newer version. It has the copy/paste and line number options. Maybe I've  missed them in 2.5.3
If I'm going to take the time to figure out how to get the most use out of it I'd rather do it with the latest version.
Thanks
Frank

[/FONT]

---

### Post by Frank P on 2019-07-03
Downloading on Windows and moving file to Ubuntu
I downloaded nano-4.3.tar.tar from [FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]https://www.nano-editor.org/download.php
After unpacking, the README says download nano-x.y.z.tar.gz. I assume it means nano-4.3.?.tar.gz but I don't know what the "Z" is replaced by.
In any case each time I download it I get nano-4.3.tar.tar which unpacks to a directory nano-4.3
Can I ignore the "z" and procede with the make
Thanks
Frank[/FONT]

---

### Post by uRock on 2019-07-03
The letters just represent the version number. Input the filename of the tar.gz package. You can bypass this by right-clicking the tarball and selecting to extract here, then us the **cd** command to get into that folder.

---

### Post by Frank P on 2019-07-04
Okay, followed all the instructions. Now it looks like I have to install (and learn) a C compiler. I think I'll revert back to the old version and leave the new one for the winter :-)
Thanks for your help
Frank

---

### Post by oldos2er on 2019-07-04
No need for that really, try ```
sudo apt-get build-dep nano && sudo apt install build-essential
``` then ```
./configure

make

sudo make install
``` assuming you want to install it system-wide. See [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

Edit: As deadflowr noted you need to enable the source (deb-src) repositories.

---

### Post by Frank P on 2019-07-04
Ran the commands
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif] sudo apt-get build-dep nano && sudo apt install build-essential
[/FONT]

Got this error
[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]E: You must put some 'source' URIs in your sources.list
[/FONT]

---

### Post by deadflowr on 2019-07-04
run
```
sudo apt edit-sources
```
you should see entries with deb-src, those are the source repositories, so they would need to be unchecked to enable.

---

### Post by uRock on 2019-07-04
I had previously installed on an Ubuntu 18.04 machine. I just installed it in 16.04. I downloaded the file and extracted it into the /home folder. Here are all of the commands I used from start to finish;

```
sudo apt-get remove nano && sudo apt install build-essential libncursesw5-dev groff
cd nano-4.3/
./configure
make
sudo make install

```After running these, I am able to open or create files using nano 4.3.

---

### Post by uRock on 2019-07-04
I created a Youtube vid of the process here; [https://youtu.be/tCM3tN6xJjo](https://youtu.be/tCM3tN6xJjo)

Let me know if you have any further issues.

---

### Post by Frank P on 2019-07-04
Followed your steps
```

[LEFT][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get remove nano && sudo apt install build-essential libncursesw5-dev groff
cd nano-4.3/
./configure
make
sudo make install
[/FONT][/COLOR][/LEFT]

```[LEFT][COLOR=#000000][FONT=Ubuntu Mono]

Success !!!!!!

Thanks!!!
Frank

[/FONT][/COLOR][/LEFT]

---

### Post by uRock on 2019-07-04
That's awesome!

---

