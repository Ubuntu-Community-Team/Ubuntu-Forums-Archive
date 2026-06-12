---
title: "http://ubuntuforums.org/images/smilies/confused.gi fHelp for a new user"
date: 2008-02-19
forum: General Help
---

### Post by Arkas on 2008-02-19
Iam a total newbie to Linux and have installed Ubuntu 7:10.


I have posted this Question before and have followed the instructions given. ( Just type in the password )

The Installation of Ubuntu is working and i get ask to remove the install disc to re-boot.

Ok this where i am haveing the problem, It ask for the Ubuntu login, which i type in then hit enter, then asks for the password, so i type that in aswell and get "Incorrect password".

I have installed Ubuntu many times now and cannot work out why the password is not being accepted.
Ive typed in the correct password in upper and lower case and also the same for the login.

I am unable to get pass this, is there a way to disable the security measures.

What should i do ???

Please help and many thanx in advance

---

### Post by amingv on 2008-02-19
Make sure you're typing your password correctly. It is equally important to type your username correctly, letter by letter. If your password/username has numbers remember that num-lock might not be enabled at boottime, so make sure all the characters are typed in.

If all the above fails, try resetting your password: reboot your PC, and before Ubuntu begins to load press the ESC key, you'll get a list, select the item that says "recovery mode" when it finishes loading type
```
passwd <your_username>
```
at the prompt, type in a new password, take care of all the characters, confirm it.
Next type
```
shutdown now -r
```
your PC will reboot, try to login with your new password.

---

### Post by Arkas on 2008-02-19
Thankyou very much amingv,

Change pw successfully 

Ive tried all the above and also to miminise all chances i left my pw as the "m" , that has even failed and i continue to get the screen that says;

Ubuntu comes with ABSOLUTELY NO WARRENTY, to the exent permitted by applicable law.
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for more details.

matty@ubuntu:~$


Im so lost, any other suggestions, Is this a common problem ?

I have reinstalled several times.

Thanks again

---

### Post by amingv on 2008-02-19
It looks like you _are_ able to log in, you are just not getting an X session (graphic environment). Perhaps by accident you installed the server edition, instead of the desktop one?

Try running this command (after you log in):
```
startx
```
If that gives you an error message, tell me what it says, if it says "command not found", type in
```
uname -r
```
it should output <some_numbers>-generic, if it shows up as <some_numbers>-server, you probably installed the server edition by accident.

**also**: Never explicitly give your password up, not even in a request for help.

---

### Post by Arkas on 2008-02-19
Thanks again amingv,

Yes it is the server addition, so to run the server addition must i install the desktop version first?

Thanks for the advice on showing my PW and I was going to quickly change that on the machine its installed to which is not on the net at this stage.

---

### Post by hahahan on 2008-02-19
Try to type : startx [enter]

Your xserver should star then, if not your /etc/X11/xorg.conf is faulty.

Regards.

---

### Post by Arkas on 2008-02-19
Thanks hahahan

Umm ( dont luagh) but were do I type that in , do I type that instead of my password or in safe mode, yes im green as green in the world of  noob of Linux.

Thanks again

---

### Post by amingv on 2008-02-19
Do you wish to run a server or a desktop machine?
Servers don't have a GUI (Graphic User Interface) by default. It is considered better by many, but you will have a hard time if you're a newbie to GNU/Linux.
If you want to run a server with a GUI, you can use one of these (will take some time to download, needs a working internet connection):

for Gnome:
```
sudo apt-get install ubuntu-desktop
```
for KDE:
```
sudo apt-get install kubuntu-desktop
```
for XFCE (I'd recommend this for a server):
```
sudo apt-get install xubuntu-desktop
```

If you want to run it as a desktop machine, go to this webpage:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
and make sure you choose the desktop edition, reinstall from there and you should be fine.

---

### Post by Arkas on 2008-02-19
Thankyou very much hahahan

You are on the money, the file startx was not installed so now im installing it. Makes me wonder it wasnt installed in the first place or where i went wrong ?


thanks again and hopefully this works

How do I thankyou guys for your posts in your profiles.

---

### Post by Arkas on 2008-02-19
thanks heaps guys, 

I would i would like to do is run a web page and also a server, but mainly a web page where ppl can d/l files and get live streaming. Am i going in the right direction?

---

### Post by amingv on 2008-02-19
Yes you can do what you want in a server, but servers are quite different from desktop installations. You will have to do a bit of tweaking and you will have to see the command line more than once (even if you install a GUI), of course, don't hesitate to ask if you step in a hard corner. I'm no server expert myself, but there's a good deal of knowledgeable people here that will help you.

Don't install startx just like that, because you still won't have a desktop environment, use one of the methods I described in my last post.

I insist that if you have never used a Unix like system (ie Linux) you should read some documents before you put your server online. It's not difficult and I promise you won't get bored out of your gourd, but it is highly recommendable. Here are some you might like:

The Official Ubuntu server guide:
[http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)
(very basic information, read the first pages and then look for information on the services you want to run)

LinuxCommand.org
[http://linuxcommand.org/](http://linuxcommand.org/)
(this will help you learn the basics of the terminal and shell scripting, as well as an insight on your new Linux OS)

The apache server guide:
[http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/)
(Apache is THE server by excellence to serve webpages and web content. and a Jewel to Open Source)

Just do not read them all at once. Take your time and have fun

Finally, if you're serious about running a Linux server, I believe you would benefit from having (and using) a desktop edition of Ubuntu in another computer. You don't have to eliminate your current OS if you don't want to, there are other alternatives like Wubi or a virtual machine. Ask me if you're interested.

---

