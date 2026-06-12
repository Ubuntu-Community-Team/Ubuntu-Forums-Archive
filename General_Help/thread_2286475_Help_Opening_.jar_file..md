---
title: "Help Opening .jar file."
date: 2015-07-12
forum: General Help
---

### Post by noah24 on 2015-07-12
Recently I've switched over from kubuntu over to xubuntu. I used to play minecraft on kubuntu when I was bored and I new the process to running it (right click and set permissions to executable) But when I downloaded it on xubuntu and went to right click there was no "executable" box. All the other programs I have have a checkbox. So i went into the terminal and made it executable from there. I tried double clicking it this time but instead of giving me this executable bit error it does nothing. So I run it from the terminal and this is what I got.
(trusty)nkknoah@localhost:~$ cd /home/nkknoah/Desktop
(trusty)nkknoah@localhost:~/Desktop$ ./Minecraft.jar
./Minecraft.jar: line 1: $'PK\003\004': command not found
./Minecraft.jar: line 2: $'\b\b\222t\354B\002': command not found
./Minecraft.jar: line 3: syntax error near unexpected token `)'
K-*&#65533;&#65533;&#65533;&#65533;R0&#65533;3&#65533;&#65533;&#65533;M&#65533;&#65533;&#65533;u&#65533;I,.&#65533;R&#65533;K-&#65533;&#65533;&#65533;&#65533;KM.JL+&#65533;K&#65533;&#65533;/).)J,&#65533;s&#65533;&#65533;x&#65533;x&#65533;PK'-.&#65533;
(trusty)nkknoah@localhost:~/Desktop$ ^C
(trusty)nkknoah@localhost:~/Desktop$ '-.?
> (trusty)nkknoah@localhost:~/Desktop$ 
> 

Can someone help me and explain what that means? Is that why mc wont open?

---

### Post by Duncan_Bristow on 2015-07-12
Try launching the executable with java -jar [path to minecraft.jar]
This is most likely due to kubuntu autodetecting the file as a java executable, and properly launching it, while xubuntu is looking at it like a raw executable. Since java needs to be interpreted into machine code, xubuntu cannot launch the file.

---

### Post by Bucky Ball on 2015-07-12
Could be off the mark here, but you have .Minecraft. Have you tried .minecraft, no capital? The command would be case sensitive. Generally it is not capitals.

i.e.  ./minecraft.jar

Also, is that a hidden file? If so, shouldn't it be:

 /.minecraft.jar

---

