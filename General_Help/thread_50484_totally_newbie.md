---
title: "totally newbie"
date: 2005-07-20
forum: General Help
---

### Post by medivh on 2005-07-20
I have just installed ubuntu on my system as secound operating system.And i have some questions.

First where can i get general knowledge about linux.How to install programs from sourcecodes etc.

1-Which programs should i install to run my works movie player mp3,ogg player, msn clone ... I know ubuntuhave them but i want the best and latest ones.I installed firefox  1.06 myself but it was easy.It has automated installition.

2-I am a computer engineering student and next year i ll be in 2. class.Which tools should i use for c++ and java editor,compiler or ide.

3-How can i see ntfs partitions.I saw them with other distributions but i cant in this one.

---

### Post by DJ_Max on 2005-07-20
[QUOTE=medivh]I have just installed ubuntu on my system as secound operating system.And i have some questions.

First where can i get general knowledge about linux.How to install programs from sourcecodes etc.

1-Which programs should i install to run my works movie player mp3,ogg player, msn clone ... I know ubuntuhave them but i want the best and latest ones.I installed firefox  1.06 myself but it was easy.It has automated installition.

2-I am a computer engineering student and next year i ll be in 2. class.Which tools should i use for c++ and java editor,compiler or ide.

3-How can i see ntfs partitions.I saw them with other distributions but i cant in this one.[/QUOTE]
 1.) apt-get
2.) You'll want the headers and development packages, use the g++ and gcc compilers. Do a
```
sudo apt-get install build-essential
``` 
For an IDE, look at Anjuta for C/C++ and Netbeans for Java.
3.) [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

### Post by noodle on 2005-07-20
For the msn clone you could use gaim. 

Personally I prefer Kopete (no reason except messages look good). Just search for it in synaptic.

To install java and the java development kit (1.5) try:

```
sudo apt-get install sun-j2re1.5
sudo apt-get install sun-j2sdk1.5
```

However the SDK is 146MB and JRE is 84.7MB, so it might take a while.

---

