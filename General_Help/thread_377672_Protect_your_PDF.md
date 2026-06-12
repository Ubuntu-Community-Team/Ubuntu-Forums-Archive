---
title: "Protect your PDF"
date: 2007-03-06
forum: General Help
---

### Post by Elena678 on 2007-03-06
Hi all, is there somboddy who knows how you can put a password on your pdf files.

okei, when this is realy not working, i also can put it in a tar.gz , or somthing like that, and protect that with a pw, but i also don't know how to do that, please can somboddy give me some help.

for all the help, a big thanks and a big hug :P

greetings

Elena

---

### Post by tribble222 on 2007-03-06
I did a quick search on the forum and found this thread which may interest you [http://ubuntuforums.org/showthread.php?t=336370&highlight=gui+encryption](http://ubuntuforums.org/showthread.php?t=336370&highlight=gui+encryption)

---

### Post by Elena678 on 2007-03-10
mmm, in did a try with that program, and it changed the extention of my file, and i could not open it self annymore :S

but in fact it is not what i need

I need to can send a psf to an other person, but there is some info in that other people not need to know, you know, jobsecret, so you also need to open in on a windows computer. i know when you use windows, you can put a code on your pdf file when you create it, and with winzip, you also can create a code when you create a zip

i just need the same for linux

if somboddy know a awnser on my question, please help me

thanks a lot

greetings

---

### Post by Albinodrew on 2007-03-10
Hi Elena678, 

If you are creating a PDF using OpenOffice, save a copy first, then go to File > Export to PDF

A dialog box open
Choose a file name, chose PDF, click OK

an other dialog box will open
go to the Security, select the first one (encrypt the pdf), then click on CHOOSE A PASSWORD
enter a password the click OK

Now click EXPORT (at the bottum)
Now you have a encryptes PDF witch need a password to be open.

To encrypt youe PDF in an archive use File Roller (should be under Application > accesoires)

Under Archive choose New, then  under EDIT scroll to PASSWORD (choose a password)

then add your pdf or wathever you want

Now you have a Achive that need a PASSWORD to open it.

I hope this will help.

P.S.: I'm  using the french version of Ubuntu, so some terms may be different on your System.

---

### Post by Elena678 on 2007-03-10
Hi, thanks for the info, i tink that's where i am looking fore :)

only one problem, in my seccond dialog box is no security section :(
[img]http://img255.imageshack.us/img255/6306/snapshot1wt0.png[/img]

do i need to install somthing more to have that?

greetings

---

### Post by Albinodrew on 2007-03-10
Hi again,

It does not look like what i have indeed.

[[IMG]http://img50.imageshack.us/img50/9454/capture2vy8.th.jpg[/IMG]](http://img50.imageshack.us/my.php?image=capture2vy8.jpg)

Do you use Ubuntu or Kubuntu, and what is your version of Openboffice.

I'm on Ubuntu Edgy with Openoffice 2.0.4

---

### Post by Elena678 on 2007-03-10
looks like there is the difference :)

I installed with the ubuntu dapper disk, so i have ubuntu 6.06 i tink :)
after that i installed the kubuntu-desktop, that is version 0.86 (mmm, why is this not 6.06, okei, what ever)
I also use not the same version of openoffice, where did you find Openoffice 2.0.4, I have Openoffice 2.0.2-2ubuntu12.2 or somthing like that :)

greetings

thx

---

### Post by khedron on 2007-03-10
[IMG]http://www.picoodle.com/view.php?srv=img03&img=/7/3/10/f_oopdfm_3949428.png[/IMG][IMG]http://img516.imageshack.us/my.php?image=oopdfun1.png[/IMG]_[[IMG]http://img516.imageshack.us/img516/1228/oopdfun1.th.png[/IMG]]("http://img516.imageshack.us/my.php?image=oopdfun1.png")_
I also have the password option. Here are what packages I have related to openoffice:

```
 
~ $ aptitude search openoffice | grep '^i' | awk '{print $2}'
openclipart-openoffice.org
openoffice.org
openoffice.org-base
openoffice.org-calc
openoffice.org-common
openoffice.org-core
openoffice.org-draw
openoffice.org-help-en-us
openoffice.org-impress
openoffice.org-java-common
openoffice.org-kde
openoffice.org-l10n-common
openoffice.org-l10n-en-gb
openoffice.org-l10n-en-za
openoffice.org-math
openoffice.org-style-crystal
openoffice.org-style-default
openoffice.org-thesaurus-en-us
openoffice.org-writer
~ $   

```Are you missing any of those? You don't have to install all of those to get pdf, I'm just including all the packages I have. Maybe also the **psutils** package?

---

### Post by khedron on 2007-03-10
OOo 2.0.4 comes standard with Ubuntu 6.10. I'm not sure if the 6.06 distro is supposed to have up-to-date packages or not.

---

### Post by Elena678 on 2007-03-10
> **khedron said:**
> [IMG]http://www.picoodle.com/view.php?srv=img03&img=/7/3/10/f_oopdfm_3949428.png[/IMG][IMG]http://img516.imageshack.us/my.php?image=oopdfun1.png[/IMG]_[[IMG]http://img516.imageshack.us/img516/1228/oopdfun1.th.png[/IMG]]("http://img516.imageshack.us/my.php?image=oopdfun1.png")_
I also have the password option. Here are what packages I have related to openoffice:

```
 
~ $ aptitude search openoffice | grep '^i' | awk '{print $2}'
openclipart-openoffice.org
openoffice.org
openoffice.org-base
openoffice.org-calc
openoffice.org-common
openoffice.org-core
openoffice.org-draw
openoffice.org-help-en-us
openoffice.org-impress
openoffice.org-java-common
openoffice.org-kde
openoffice.org-l10n-common
openoffice.org-l10n-en-gb
openoffice.org-l10n-en-za
openoffice.org-math
openoffice.org-style-crystal
openoffice.org-style-default
openoffice.org-thesaurus-en-us
openoffice.org-writer
~ $   

```Are you missing any of those? You don't have to install all of those to get pdf, I'm just including all the packages I have. Maybe also the **psutils** package?

```

openclipart-openoffice.org
openoffice.org
openoffice.org-base
openoffice.org-calc
openoffice.org-common
openoffice.org-core
openoffice.org-draw
openoffice.org-evolution
openoffice.org-gnome
openoffice.org-gtk
openoffice.org-help-en-us
openoffice.org-help-nl
openoffice.org-help-ru
openoffice.org-help-sv
openoffice.org-impress
openoffice.org-java-common
openoffice.org-kde
openoffice.org-l10n-common
openoffice.org-l10n-en-gb
openoffice.org-l10n-en-us
openoffice.org-l10n-en-za
openoffice.org-l10n-nl
openoffice.org-l10n-ru
openoffice.org-l10n-sv
openoffice.org-math
openoffice.org-thesaurus-en-us
openoffice.org-writer

```

i tink i miss 
openoffice.org-style-crystal
openoffice.org-style-default

but i also don't see them in adapt :S
(but i tink style is not that importent)

thanks for the info

---

### Post by Elena678 on 2007-03-10
> **khedron said:**
> OOo 2.0.4 comes standard with Ubuntu 6.10. I'm not sure if the 6.06 distro is supposed to have up-to-date packages or not.

then i tink i need to start with downloading 6.10 :)

i will post it when if it works there, or not.

can taking some time, i have not a perfect connection :)

thanks for the help :)

---

