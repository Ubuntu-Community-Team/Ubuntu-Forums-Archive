---
title: "Can some one help me set up Iceweasel? (Solved)"
date: 2006-10-11
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2006-10-11
I have tried to follow the how-to but get confused. I have downloaded and extracted Iceweasel and it is in temp folder. I do not know what to do from here. Please, I need **VERY** simple terms as I am still new to this and I do not want to **break** my system again!

---

### Post by kane77 on 2006-10-13
try: "sudo apt-get install iceweasel32" (or iceweasel)

---

### Post by motang on 2006-10-13
> **MustangSallydd said:**
> I have tried to follow the how-to but get confused. I have downloaded and extracted Iceweasel and it is in temp folder. I do not know what to do from here. Please, I need **VERY** simple terms as I am still new to this and I do not want to **break** my system again!

Try this [out]("http://www.ubuntuforums.org/showthread.php?t=270631&highlight=iceweasel")!

---

### Post by IusedTObeSOMEONEelse on 2006-10-13
I tried the sudo thing and got this:             $ sudo apt-get install Iceweasel
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Icewease     ** Exactly ****what do I put  in where it says :: the_directory_where_you_ want_iceweasel_installed**                                                                       **tar -xvf iceweas -C the_directory_where_you_want_iceweasel_installed)**

---

### Post by IusedTObeSOMEONEelse on 2006-10-14
Excuse me, **Bump**!

---

### Post by K.Mandla on 2006-10-14
Hi. There are two ways of installing Iceweasel via that thread: You can download a zipped package, or you can use Kilz's prepackaged deb. The latter is the easier of the two.

Try this: Follow [this link]("http://home.comcast.net/~ubuntu64user/iceweasel-1.5.0.7-ubuntu-i386.deb") to download Kilz's deb. You should get a download dialogue; save it whereever you feel is a good place. The home directory is fine.

Now open a terminal window. You'll have to navigate to where you downloaded the deb file. If you type 

```
ls
```
you should see the file in the directory listing. When you've found it, type

```
sudo dpkg -i iceweasel*.deb
```
After a few seconds (probably less), you should have it installed. If you see error messages at that point, there might be something else going on.

From there, you should be able to type "iceweasel" and the browser will spring into action, like a ninja. ;)

If you still have problems with it, feel free to reply here. You can PM me too, or one of the other moderators could probably help. Kilz is very helpful as well. :)

---

### Post by IusedTObeSOMEONEelse on 2006-10-14
Thanks for reply! When package installer opens, an error box pops up:** Could not open 'iceweasel-1.5.0.7-ubuntu-i386.deb'The package might be corrupt or you are not allowed to open the file. Check the permissions of the file.**   That what it says.

---

### Post by K.Mandla on 2006-10-14
> **MustangSallydd said:**
> Thanks for reply! When package installer opens, an error box pops up:** Could not open 'iceweasel-1.5.0.7-ubuntu-i386.deb'The package might be corrupt or you are not allowed to open the file. Check the permissions of the file.**   That what it says.
Interesting. Let's try it a slightly different way.

Type (or cut and paste) this into a terminal window.

```
wget http://gnuzilla.gnu.org/download/iceweasel-1.5.0.7-g1-i386.tar.bz2
```
That will download the iceweasel package for you. Next, type

```
tar -xvf iceweasel*
```
That should uncompress the package, and put everything into a folder called *iceweasel-1.5.0.7-g1-i386*. Now try this

```
cd iceweasel-1.5.0.7-g1-i386
./iceweasel
```
Let's see what happens. Iceweasel *should* pop up on your screen after a second or two. Keep your fingers crossed. [-o< :-P

---

### Post by IusedTObeSOMEONEelse on 2006-10-14
Thank you So Much! :D  That did it, Thanks K. Solved

---

### Post by K.Mandla on 2006-10-14
Excellent! :D :D :D Let me know if you have problems setting it as your default browser. Cheers! 

(Marked as solved.)

---

### Post by IusedTObeSOMEONEelse on 2006-10-14
I am working on that now. I went to preffered applications and it set itself to custom. now it didn' show up in Applications>Internet. How can I fix that so I can make a task bar launcher? Also I'm trying to get gnash. Reading forum on that. Thanks, Sally

---

### Post by K.Mandla on 2006-10-14
That's okay. If you found the iceweasel shell script and selected it from the Preferred Applications dialogue, then it should start Iceweasel every time you pick Internet from the Applications menu.

Remember to edit your desktop icons too. Chances are the blue globe at the top will still point at Firefox; that's because (unless I'm mistaken) the icon is set independently of the desktop's preferred browser.

I'm afraid I can't help with gnash; I've never used it.

Cheers! :D

P.S.: I think if you right click on the taskbar, you'll get the option to add a new launcher button. Just set that one up to point at Iceweasel. :)

---

### Post by dolphinsonar on 2006-10-19
> **K.Mandla said:**
> Hi. There are two ways of installing Iceweasel via that thread: You can download a zipped package, or you can use Kilz's prepackaged deb. The latter is the easier of the two.

Try this: Follow [this link]("http://home.comcast.net/%7Eubuntu64user/iceweasel-1.5.0.7-ubuntu-i386.deb") to download Kilz's deb. You should get a download dialogue; save it whereever you feel is a good place. The home directory is fine.

Now open a terminal window. You'll have to navigate to where you downloaded the deb file. If you type 

```
ls
```you should see the file in the directory listing. When you've found it, type

```
sudo dpkg -i iceweasel*.deb
```After a few seconds (probably less), you should have it installed. If you see error messages at that point, there might be something else going on.

From there, you should be able to type "iceweasel" and the browser will spring into action, like a ninja. ;)

If you still have problems with it, feel free to reply here. You can PM me too, or one of the other moderators could probably help. Kilz is very helpful as well. :)


Hey thanks!  This was definitely the easiest way to install ice weasel.  Newbies like myself will probably get confused with the other post that is currently floating around.  I am not sure how to install things without synaptic, but this was fairly simple  THanks!

---

