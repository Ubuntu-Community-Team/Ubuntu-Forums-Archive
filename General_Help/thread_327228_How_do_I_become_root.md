---
title: "How do I become root"
date: 2006-12-28
forum: General Help
---

### Post by here4real on 2006-12-28
im the owner but ubuntu thinks im not so it wont let me do some stuff :mad: :mad: :mad: 

dont say switch to the right user because i only have 1 of them

any one know how to fix ???????????

---

### Post by ComplexNumber on 2006-12-28
fix what? :confused:

---

### Post by NeoLithium on 2006-12-28
I'm pretty sure you need to be root user for some of these things. In that case, enter the password that you set up for yourself; when it asks you for that, and you're in.

You're not the technical "owner" of your whole system; many important things belong to root; so the average user doesn't delete or modify something by accident, and to protect things over a network as well.

---

### Post by PilotJLR on 2006-12-28
Please read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Things that can hurt the system require root, or superuser, privileges. It's one of the means unix/linux uses to keep a large multiuser system safe. Helps for single user systems too, since it effectively blocks the virus / spyware threat!
(this is a simplification, but you get the idea)

Based on the name of this thread, also please see the attached file.

---

### Post by here4real on 2006-12-28
where is root sudo on ubuntu 6.06????

---

### Post by meng on 2006-12-28
Have you read the link or not? What don't you understand?

---

### Post by PilotJLR on 2006-12-28
Please tell us exactly what commands you are typing in that are not working.

You basically type "sudo" in front of them to become root, as the link I provided explains to detail. Use this with care.

Avast matey!

---

### Post by here4real on 2006-12-30
what commands ???????????

i didnt type any commands ? :confused: :confused: :confused:

---

### Post by ~LoKe on 2006-12-30
Perhaps Linux isn't right for you.

---

### Post by _simon_ on 2006-12-30
What are you trying to **DO?**

---

### Post by koenn on 2006-12-30
This is going to be an interesting thread to watch. Very descriptive title, clean an neat discription about the nature of the problem, 4-5 people willing to help and having a hard time getting any information or useable feedback ... 
better than anything on TV right now.

---

### Post by Ramses de Norre on 2006-12-30
Let's keep it friendly..

Could you just describe your problem as clearly as possible? It's pretty hard to help if we don't know exactly what the problem is.

---

### Post by riven0 on 2006-12-30
here4real, listen; everyone wants to help. But we can't if you don't tell us what you are doing. Are you trying to log in? Install a program? Install Ubuntu? What exactly are trying to do?

---

### Post by derjames on 2006-12-30
> **koenn said:**
> 
better than anything on TV right now.

I think so...

---

### Post by peebly on 2006-12-30
The suspense is killing me, so I will make a guess.

Are you trying to add files etc, to the folders in the file system.

;)

---

### Post by koenn on 2006-12-30
> **Ramses de Norre said:**
> Let's keep it friendly...
That *was* friendly. 
I mean - with "Aaarg" for a title and "it won't let me do stuff" for problem description ... ?

(But let's not drift too far off topic )

---

### Post by ~LoKe on 2006-12-30
> **koenn said:**
> That *was* friendly. 
I mean - with "Aaarg" for a title and "it won't let me do stuff" for problem description ... ?

(But let's not drift too far off topic )

As far as I'm concerned, a topic has yet to be established.

---

### Post by d3v1ant_0n3 on 2006-12-30
We could just start listing solutions to common problems and hope one of them is the right one?

---

### Post by koenn on 2006-12-30
> As far as I'm concerned, a topic has yet to be established.
LOL

> We could just start listing solutions to common problems and hope one of them is the right one?
OK, I'll have a go: 

1- To do stuff, sometimes you just click on the thing and the stuff works. Sometimes it won't let you do stuff but asks a password. If it asks a password, give it ***your*** password and it will let you do the stuff. 

Or, in other words: 
> **NeoLithium said:**
> I'm pretty sure you need to be root user for some of these things. In that case, enter the password that you set up for yourself; when it asks you for that, and you're in.l.

2- To do other stuff, such as work with files, sometimes you need to be the owner of that file. If you are not the owner, there is still other stuff you can try to solve it but to be able to explain the stuff you need to fix it, people on this forum will have to know **exactly ** what it is you're trying to do (as mentioned in a few posts already) before they can tell you how to fix stuff.

---

### Post by radu_chindris on 2006-12-30
I guess that he's just upset that someone(thing) dares to ask him for a password to do stuff ;)

---

### Post by bulldog on 2006-12-30
And he bailed out already........................:(

You guys have to learn to recognize a frustrated user, you know how easily they are scared and run away.:-)

---

### Post by koenn on 2006-12-30
> 
Dear Frustrated User

4. Rephrase your post. Sometimes if you give too little information or too much information (especially with no paragraph breaks), people just don't want to spend the extra time to understand what you're saying. Meet people half-way, and they'll more than likely meet you half-way and go beyond that half-way mark.
[http://ubuntuforums.org/showthread.php?t=82471](http://ubuntuforums.org/showthread.php?t=82471)

---

### Post by PilotJLR on 2006-12-30
Honestly, here4real, tell us exactly what you are trying to do, and we will help you. Please be as detailed as you can.

Vague words like "stuff" won't work... so just let us know exactly what you need to get done.

---

### Post by here4real on 2006-12-30
i want to use the sudo thing to make my computer reconginze me as the superuser (root)
because i want to have permisson to change some stuff

](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by haxer on 2006-12-31
Open up the "terminal"  when you get it opened write sudo then your "root" password be careful now the password wont be shown ********** it will just be blank!! ;)

---

### Post by here4real on 2006-12-31
do you mean from the Applications tab because it just did this

joey@joey-desktop:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
joey@joey-desktop:~$

and when i typed my password it showed up and didnt do anything



thanks for trying to help me    wow 3 pages your much more helpful than those linspire guys:D :D :D :D :D :D :D :D

---

### Post by spockrock on 2006-12-31
ok sorry can you specifically tell use what you are trying to do, so we can properly tell you how to use sudo, so you can learn to use sudo properly.

for the most part everything out side your home directory is owned by the root user, this is for security reasons.  so if you wanted to edit a config file like xorg.conf in terminal you would do;

gksudo gedit /etc/X11/xorg.conf

hope this kinda makes sense, so please tell us exactly what you want to do, so we can tell you exactly how to use sudo.....

---

### Post by riven0 on 2006-12-31
> **here4real said:**
> do you mean from the Applications tab because it just did this

joey@joey-desktop:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
joey@joey-desktop:~$

and when i typed my password it showed up and didnt do anything



The problem here is that just typing sudo will do nothing; you have to use it with a command. Like say you want to install something. If you just do:
> 
apt-get install firefox

It won't work because you don't have superuser permission to install, so you have to do:

> sudo apt-get install firefox

Then bash will ask for your password and it will work.

If you want complete root access without having to input sudo and your password everytime, then do:
> 
sudo -s -H

Note, though, that when you close the terminal down you'll lose root permission and you'll have to do it all over again.

---

### Post by PilotJLR on 2006-12-31
Is this flamebait, or are you being serious? Did I not just ask for specific information, instead of "i want to do stuff?"

On page 1, I gave you a link that explains exactly how to use sudo. READ IT.


> **here4real said:**
> i want to use the sudo thing to make my computer reconginze me as the superuser (root)
because i want to have permisson to change some stuff

](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by bulldog on 2006-12-31
> **here4real said:**
> i want to use the sudo thing to make my computer reconginze me as the superuser (root)
because i want to have permisson to change some stuff

](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

Well if you have to ask how you can change 'stuff' it seems to me you haven't that much experience with linux
That said,you can ask yourself if it's wise to go changing 'stuff',because I think you haven't the slicest idea you can destroy your install in a split second.

But you ask and we answer,but you're warned.
Hit ALT+F2 and type in the box gnome-terminal,and type in the new terminal window sudo -s.
You're root know and able to whipe out your install,so beware,it won't ask for confirmation,it just does.

If you prefer a graphical way to do your 'stuff' hit ALT+F2 again and type gksudo nautilus
Now you're able to do your 'stuff' with the file browser,the warning still stands though.

---

### Post by tseliot on 2006-12-31
I have changed the title of this thread.

Please use a more explicit title next time.

---

### Post by rsambuca on 2006-12-31
ahhh:confused:   This thread was way better with the old title.

---

### Post by here4real on 2006-12-31
i did the sudo -s -H thing but it still wont let me change the permissions because to still thinks i am not the owner

---

### Post by rsambuca on 2006-12-31
here4real

WHAT IS IT THAT YOU ARE TRYING TO DO?????????

---

### Post by compwiz18 on 2006-12-31
> **here4real said:**
> i did the sudo -s -H thing but it still wont let me change the permissions because to still thinks i am not the owner
I know this has been said before, but I'm going to say it again: here4real, **what exactly are you trying to do**?  We can help you so much more if you give us a specific example, such as "I am trying to change file permissions, how do I do this?"  Just asking how to become root is a hard question to answer because there isn't a definite answer - if you are using a terminal, you can do **sudo -s -H** ... if you are using the GUI, you just click a button, and your password will be asked for.

Once again, you need to tell us **exactly** what it is you want to do, otherwise we will continue to post random information about pirate keyboards ;)

---

### Post by Sef on 2006-12-31
I m locking this thread for trolling.   This is the 36 post and still the poster can't say what they want to do?  I'm not having anyone else waste their time with this poster.

---

