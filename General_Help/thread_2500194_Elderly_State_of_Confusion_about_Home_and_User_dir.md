---
title: "Elderly State of Confusion about Home and User directory /ed...."
date: 2024-08-26
forum: General Help
---

### Post by ozark_hillbilly on 2024-08-26
22.04 LTS was just installed.

I am in an elderly state of confusion about the Home directory and the username directory. In my case the user directory name is 'ed.'

I provided two screenshots showing the two instances of 'Files' displaying simutaneously:

Computer /home and Home with the little house in front of it.

The 'ed' directory is listed/highlighted under Computer /home and has the same contents of Home with the house icon.

Where am I supposed to be keeping all my personal files? Is the /ed directory even necessary if I am the only user of this system?
With this new install I want to avoid having files under the wrong directory. Or does it even matter?
Can I delete /ed or does it need to remain? 

I am confused and it is a little perturbing....lol


Solved: ***** SEE POST #4 *********

---

### Post by Quarkrad on 2024-08-26
The top level directory is **/**  - under that you have a number of standard folders in the pane called Computer such as bin, boot, cdrom, dev, etc and many more.  During the install process many folders are created under **/** to make the operating system 'work' and as such are not  used by  many standard users.   One of the folders, under **/** however, is called **home**.  This **is** the working folder/directory where users keep their personal files/folders.  If you look at your other screenshot titled **Computer /home** you will see the contents of this home folder.  This folder called **/home** (written like that because **home** and under **/** - so it is written as **/home**) has standard folders in it like Desktop, Documents, Downloads, etc.  You have already made a number of folders under **/home** already - e.g. Guns, mom and one called ed.  This folder would be written as **/home/ed** because home is under **/** and **ed** is under **/home**.  Personally I keep my personal files under **/home/Documents** but you can create and delete what you like in the **/home** directory/folder.  I think one confusion could be the file manager you are using if it displays two panes at a time.  Do you know what Desktop top version of 22.04 you are using, e.g. Ubuntu Mate, Ubuntu Gnome, KUbuntu?

---

### Post by Impavidus on 2024-08-26
/home is the directory containing the home directories of every ordinary user (unless you configure things otherwise). As you're the only normal user of your system, there's one directory in /home, being ed (full path: /home/ed) That is your personal home directory. When you click Home in the side panel of your file manager, it should take you to your personal home directory. That is where you should store your documents.

It looks like something isn't entirely right on your system (have some of the contents of /home/ed been duplicated unter /home?), but the screenshots don't provide enough information to see the details.

---

### Post by The Cog on 2024-08-26
Do **not** delete /home/ed. That is your (ed's) home directory where everything of yours should be kept. All your personal settings will be stored in there (often in /home/ed/.config, but also others).
/home is the directory where all users' homes are placed, even if ed is the only user. Lots of things will break if you delete /home/ed. And you should not even have permission to edit the contents of /home.

There is a possible source of confusion here because /home would reasonably be called **the** home directory and /home/ed would definitely be called **your** (ed's) home directory. The home icon in **your** file manager refers to **your** home directory, and every user's home icon wil link to their own personal home directory. Windows has a similar arrangement, but I think theirs is called c:/users, containing e.g. c:/users/ed and that is much less confusing.

---

### Post by maglin2 on 2024-08-26
I think the use of 'Home' and 'home' in gnome Files risks confusion.

If I use Files to look at the file system under / there is a folder called 'home'.

If I open this folder it contains (in my case) folders called  'dave' and 'dg'. 'dg' is me.

If I click on 'dg' it shows 'Home' in the address line. Under it are the standard folders (Documents, Downloads etc).

I think there would be less risk of confusion if the address line showed '/home/dg', not 'Home'.

But I doubt if the developers of Files are obtuse, and they will have thought otherwise with reason.

---

### Post by ozark_hillbilly on 2024-08-26
I am using Ubuntu Gnome AFAIK. 
"I think one confusion could be the file manager you are using if it displays two panes at a time."
I just had a second window opened under the Files app to show what I what seeing.

"This folder would be written as /home/ed because home is under / and ed is under /home."
So deleting the 'ed' folder is not going to a problem? Such as with signing on/off, etc.
I am trying to to understand if 'ed' is actually needed since I am the only person using the computer.

---

### Post by ozark_hillbilly on 2024-08-26
"It looks like something isn't entirely right on your system (have some of the contents of /home/ed been duplicated unter /home?), but the screenshots don't provide enough information to see the details."

Good eye there. I do in fact have some duplication present and was waiting to see if I should get rid of the duplicates outside of 'ed' or get rid of 'ed' and have everything under /home.

---

### Post by ozark_hillbilly on 2024-08-26
"Do not delete /home/ed. That is your (ed's) home directory where everything of yours should be kept. All your personal settings will be stored in there (often in /home/ed/.config, but also others).
/home is the directory where all users' homes are placed, even if ed is the only user. Lots of things will break if you delete /home/ed."

OK!!! A definitive clear response is what I was looking for. I will get rid of the duplicates outside of 'ed' and work within its confines.

"And you should not even have permission to edit the contents of /home."

Ok. Is that something only 'root' should be able to do? I will need to look into the current permissions of /home and see how it is configured. I did have a sign on issue and
needed to go back door through GRUB to set a root password and then login and use chown command:

chown -R ed:ed /home

Perhaps I should have  instead used ed: ed /home/ed instead.

The conumdrum I have with all this is that once I get Linux setup it is rock solid. And for the past two to three years I have had no issues with the OS. It is the old phrase "use it or lose it" 
that applies sto me. Then something ate all my root/boot partition memory and everything went downhill from there. Bleachbit normally worked to correct this but this last time it made things
unstable. I will be loathe to rely on it again in the future.

Thanks for clarifiying my confusion.

---

### Post by ozark_hillbilly on 2024-08-26
"I think there would be less risk of confusion if the address line showed '/home/dg', not 'Home'."

I tend to agree being that I am an elderly computer user who does not readily keep up with things as 
well as you younger 'whippersnappers.' ...lol...

---

### Post by ne29914 on 2024-08-26
I use Lubuntu, and have no experience with Ubuntu.
But the screenshots you show are not really nice IMO. They don't show clearly where you are in the directory tree.
I always set up two (or sometimes more) users on my systems:
1: myself (of course)
2: a Guest account. This allows others to use my PC without interfering with my stuff.
Here's my /home
:[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294147&stc=1[/IMG]

As you can see there are two users: macro (me) and abguest, Ignore timeshift, that's for backups.

And here's my personal directory, /home/macro:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294148&stc=1[/IMG]

On the top bar, you always see where you are. All my stuff is in Documents, Music, Pictures and Videos. That's where yours should be as well. Or add directories as needed.

Cheers.

---

### Post by werewulf75 on 2024-08-26
> **The Cog said:**
> There is a possible source of confusion here because /home would reasonably be called **the** home directory and /home/ed would definitely be called **your** (ed's) home directory. The home icon in **your** file manager refers to **your** home directory, and every user's home icon wil link to their own personal home directory. Windows has a similar arrangement, but I think theirs is called c:/users, containing e.g. c:/users/ed and that is much less confusing.
The Windows arrangement of 'c:\users\ed' was, IIRC, copied from some BSD derivatives that used a similar scheme, e.g. '/users/ed'. It's an awful long time ago, but if memory serves this was the case in Nextstep (Mach kernel/NetBSD), where in the GUI 'users' was shown with a double house icon and individual users with a single house icon for 'home'. I may of course be mistaken...

---

### Post by dragonfly41 on 2024-08-27
If you are of a certain age as am I you might remember [Danny Kaye in the Court Jeste]("https://www.youtube.com/watch?v=kuj5x3afeK8")r.
Many technical discussions here are like that sketch.

---

### Post by ozark_hillbilly on 2024-08-27
Thanks for sharing....

---

### Post by werewulf75 on 2024-08-27
> **dragonfly41 said:**
> If you are of a certain age as am I you might remember [Danny Kaye in the Court Jeste]("https://www.youtube.com/watch?v=kuj5x3afeK8")r.
Many technical discussions here are like that sketch.
I refuse to admit to be "of a certain age" - better by far to be of an **uncertain** age! :P (Anyway, who can really remember at this stage? ;) )

---

