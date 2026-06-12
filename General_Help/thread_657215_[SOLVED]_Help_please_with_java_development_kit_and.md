---
title: "[SOLVED] Help please with java development kit and netbeans installation"
date: 2008-01-03
forum: General Help
---

### Post by AndreiMe on 2008-01-03
i know some programming and i need c++ compiler cause i'm in college and it's my specialization.
now of course on xp, i have visual studio 2005 but on ubuntu i wanted to install netbeans cause it looked so good and felt the perfect choice.
i went for the latest version directly from the site.
then i found out it needed java development kit to run. so i (tried?) to install it. 
Firefox saves all my downloads on my desktop. and from what i read, i needed to access the files directly from the desktop. i went to desktop via the terminal, and it remained there, that is kinda annoying but i can leave with it, don't know how to restore it as it was previously.
so it installed java on my desktop. i don't like it, and don't know how to remove it. I'm currently at work on a mac so i can't show you a print screen of it but i hope you understand my problem.
when I'm trying to install netbeans it cannot find java. that is annoying. can't it be fixed. can i just purge the java installation from my desktop. please help, don't wanna code in xp unless necessarily

---

### Post by irv on 2008-01-03
I have a question?
When you downloaded java development kit, what file did you download? the .tar or .deb or ? It is best to get a .deb file and install it through the installer in Ubuntu or from a terminal.
If you did the install right, even though you downloaded it to your desktop it should have installed in the right place. After the install you could have just deleted the tar or deb file and it should run.
I do some development and I found “Eclipse” really work great in Ubuntu. You can use it for variety of different programming languages.

---

### Post by AndreiMe on 2008-01-03
well if i'm not mistaking (i hope) it was an .sh, i downloaded it directly from the site of java....
and i used the command sh... from the terminal. that's why i had to relocate myself on the desktop via terminal. and i cannot move the folder, or delete it cause i don't have privileges. so I'm stuck with it there. what is the most important question right this moment is... can i purge the install? 
and is there a step by step tutorial on how to install something like that.
and how can i restore the terminal?

---

### Post by irv on 2008-01-03
One thing you can try to delete the installed files is to go to: Application >Debian >Apps >System >X-Terminal as root. Then change to the desktop and you should have rights to delete the files that were installed there. Be careful because at this point you have full rights to do some damage.

---

### Post by AndreiMe on 2008-01-03
can you please tell me how to do this(im very new in ubuntu)
isn't there another way to do this, like uninstall?

---

### Post by irv on 2008-01-03
Once you go to Application >Debian >Apps >System >X-Terminal as root and run. It will open up a terminal window. type:
> 
[QUOTE]cd /home/your-name/Desktop

you should see a prompt:

root@ [computer name]:/home/[user name]/Desktop#

then type 

> ls

this should list all the files and folders on you Desktop.

find the file or folder you want to remove and then remove it.

you might want to type

> rm --help

to get a help with this command. be careful not to remove the wrong files or folders. This command does not put the deleted file in the trash, it just deletes it.

Here is a what my terminal looked like:

> root@irv-laptop:/home/irv# cd /home/irv/Desktop

root@irv-laptop:/home/irv/Desktop# ls

calc.rb~                    Recipe Details Report.txt~

Desktop icons               test.rb

Google-googleearth.desktop  test.rb~

Laptop Windows.desktop~     UserManual.pdf

prayers.htm~                virtualbox_1.5.4-27034_Ubuntu_gutsy_i386.deb

Proforma Invoice.xls        vnc100.sh~

root@irv-laptop:/home/irv/Desktop# rm test.rb


In my Terminal window I removed a file named test.rb.

I hope this helps you out.

Irv

---

### Post by AndreiMe on 2008-01-04
thx alot i will give it a go today.... if it doesn't work i still learned something new :D:guitar:

---

### Post by AndreiMe on 2008-01-05
im stuck :( soething elsei (i couldn't find the x terminal as root -->me new at this ):(

---

### Post by onero on 2008-01-05
Jst install the sun-java6-jdk package in Synaptic to install the JDK. Then just install Netbeans 6 by running the .sh file (downloaded from Sun) :D I'm not sure about how to remove the JDK downloaded from Sun's site though. Most things can be found in the repos, and it's usually best to install from there.

---

### Post by AndreiMe on 2008-01-06
thanks solved it :D

---

### Post by Elegorod on 2008-01-06
> **AndreiMe said:**
> thanks solved it :D

You could show it to anyone. Choose Thread tools - Mark this thread as solved, please.

---

