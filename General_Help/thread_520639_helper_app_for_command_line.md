---
title: "helper app for command line"
date: 2007-08-08
forum: General Help
---

### Post by flygin on 2007-08-08
Just finished a helper application for the console.


[http://www.geocities.com/thierryguy/angelscript.html](http://www.geocities.com/thierryguy/angelscript.html)

the app (shell script) provides you with information about installation and whatever else and gives you the commands with options to use. 
the console is always *FREE*, you are not in an application, you are with it. 

I am looking for some feedback.

The full ubuntu unofficial starter guide
is available as scripts. No more copy and paste between the browser and the console. 


(ps: no guaratee about bugs, beta version)
PS: if someone could explain me how to upload to sourceforge, I would really appreciate it (I have an account, yes...)

---

### Post by flygin on 2007-08-08
wow! this is really great!

---

### Post by apetresc on 2007-08-08
Wow! This is a great idea. I'm at work right now so I can't test it out just yet, but it looks like a keeper =D>

You should consider moving this project somewhere a little more permanent than Geocities. You could apply for a Sourceforge account and I'm sure you'd get it. Or you can go for a Google Code account and get that instantly.

Great work!

EDIT: Oh, I just read that you already have a sourceforge account. However, you not only need an account, you need to apply for a PROJECT. You can do that here, with instructions: [https://sourceforge.net/register/](https://sourceforge.net/register/). Once that is approved, your project will have its own "Project Page". Once that's up, you'll need to upload your code using Subversion. If you don't know how to do that, post here and I'll walk you through it :)

---

### Post by flygin on 2007-08-12
yes, subversion is were I was lost. Project is approved about 2 month ago.

any help is welcome!

---

### Post by flygin on 2007-08-12
Generally speaking:
can I get a hml-page at sourceforge. It looked like (angelscripts.sourceforge.net) but again I could not find any way to upload anything.

I have virtually no knowledge about CVS. can you recommend me a page?

again, any help is welcome!

---

### Post by flygin on 2007-08-25
sorry, just found a bug (there was a dead link)

fixed.

angelscript also need gawk (awk is not enough) 

Update:
no more awk, gawk, xmlstarlet needed. Just sed

---

### Post by flygin on 2007-11-12
angelscripts are on sourceforge!

[http://angelscripts.sourceforge.net/](http://angelscripts.sourceforge.net/)

!long live the command line!

---

### Post by flygin on 2008-01-16
ANGEL-SCRiPTS is a framework to get help on the console. It is especially suited for tasks that demand more than one command to be set up, like mounting a samba share, exporting a nfs directory, or similar. Such tasks are contained in an angel-script (or angel).
The angels (scripts) are located in a directory (basedir) with subdirectories to allow grouping by subject. Multiple base directories are possible (change with angel-basedir). Angels are called by just typing ``angel'' (to see the base directory), by referring to the name including its path (without base directory) or by the find-option.
ANGEL-SCRiPTS will then display the file - in case it is a file - or the contents of the folder, if the choice is a folder.
The new concept is that after any invocation of angel-scripts you are always back on the console. Angel-script uses the numbers 1 to 255 and the letters b,f,r,u,n,p *as commands* for navigation, i.e. after each step angel-scripts brings you back to the console to use your own commands. You are not *in* the application - you're with it.
This allows for additional commands, checking of files, etc. or simply use only those commands that you need.

---

### Post by flygin on 2008-01-16
ANGEL-SCRiPTS are for those who do not remember exact parameters by heart or do not want to remember ten commands including the parameters. 

It it is a way to explain an installation processes with the ease that the person using it does not have to retype or copy-and-paste all the time.

As angels are basically just lists of commands with some informational text. The commands are accessible from the console by just typing their respective number.

Advantages:
[LIST]
[*]The commands are seen *within* the console - no flipping of screens.
[*]The commands are accessible. 
[*]The commands can be edited as needed.
[*]The command line is always free.
[/LIST]

---

### Post by flygin on 2008-01-16
Countless websites and articles in magazines explain installations or similar  with a handful of commands to be used on the console. 
This results in nasty switching of windows and copy-paste actions. Worse, if you have to be on runlevel one, there's no more http.

With angelscripts: 
[LIST]
[*]Read the article (on- or off-line)
[*]Open the console
[*]download the corresponding angel for the article 
[*]Call the angel
[/LIST]
All  the commands of the article are *at your fingertips* in the console (plus information about).

---

### Post by flygin on 2008-01-16
This is a example for changing samba workgroup.

---

### Post by flygin on 2008-01-16
I am really tired of always copy and paste between my browser and the command line when I have to do an installation. The man pages do not give me only help for single commands but not for entire processes. What can I do?

ANSWER:
use angelscripts!

---

### Post by flygin on 2008-01-16
We have a large network and many tasks after set by our experts have to be repeated by newbies. The tasks involve about 10 commands on the command line with different parameters but the general process is always same. The problem is that our newbies do not know the tasks and have to be told always anew. 

Is there a way to bring interactive help to the command line so that less experienced users can do installations and system maintenance?

ANSWER: yes, there is, use ANGELSCRiPTS

The angels are organised in a directory structure. There is also a find function. Once an angel is set up, every newbie can use it. ANGELs also include adaptability.

---

### Post by flygin on 2008-01-16
All our articles include a bunch of commands to be used on the console. However, the readers complain that they do not like to enter all the commands or copy them from the website. Is there a way to offer commands and short information on the command line. How can we provide the commands we explain in our articles to the command line so that the user can pick it up conveniently?

ANSWER: use ANGELSCRiPTS
ANGELSCRiPTS provide you a way to offer all the commands in an article directly to the command line *at the fingertips of the user*. More than that, ANGELSCRiPTS offer informational text as well. The whole article can be placed into an angel. All the commands are accessible easily from within the console.

---

### Post by flygin on 2008-01-16
We have more than 500mb of shell scripts to manage tasks in our company but we can't share the scripts easily because you can't find the right one and you don't know exactly what script is doing unless you open it in a text editor. 
We need a easy way to share our scripts, find them quickly directly from the command line and see what they are doing without opening a text editor. What can we to?

ANSWER: don't go for IBM, use ANGELSCRiPTS!

With ANGELSCRiPTS you can organise your shell scripts in a directory structure, find and access them easily from console according to name or keywords and you have informational messages coming with each angel. The scripts can directly be integrated into angels; the angel stores the explanation of what the script is doing. Further breakdown of the script into different angel-commands (each a shell script) allows for adaption and diversification. 
The scripts themselves can be viewed or hidden in the console with a single click.

---

### Post by flygin on 2008-01-23
at least, sourceforge:
[http://angelscripts.sourceforge.net](http://angelscripts.sourceforge.net)


(geocities will be faded out)

---

### Post by flygin on 2008-05-29
buuh!! nobody is looking at my angelscripts.

where can I post it?

---

