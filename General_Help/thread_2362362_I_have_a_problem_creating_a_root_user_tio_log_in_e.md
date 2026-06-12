---
title: "I have a problem creating a root user tio log in each time i enter to my ubuntu"
date: 2017-05-27
forum: General Help
---

### Post by elreydelaswasas1 on 2017-05-27
Firstable i run the command sudo passwd root at the terminal then i wrote my user password after that i wrote the same new asked password 2 times then i run the command su and wrote the same password as the password i talked about in this message then i  executed the cd command thenfore i executed the gedit /etc/lightdm/lightdm.conf then after i executed that command there appeared a text dcument there i replaced what there said with [SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
greeter-show-manual-login=true y replaced it with the copy paste method then i saved the document text and then i executed two times the exit command after that i rebooted the pc and there at login appeared an option that said begin session i wrote root and pressed enter after that i enter the pasword i entered twice between the part i entered the sudo passwd root comman finally the su command and there appeared the next problem There appeared an error uploading <</root/.profile>> mesg: ttyname there failed: ioctl non appropiate Function for the device 
As result the session misconfigured Correct the issue as soon as possible

---

### Post by oldos2er on 2017-05-27
Duplicate of [https://ubuntuforums.org/showthread.php?t=2362358](https://ubuntuforums.org/showthread.php?t=2362358) closed. Please don't create more than one thread for each question or problem you have.

---

