---
title: "How do I get to &quot;download&quot; ?"
date: 2021-06-18
forum: General Help
---

### Post by anneranch on 2021-06-18
OK , I bypass "File manager" phony security by  command 
sudo nautilus 

That gets me to "snap" which I have no clue what it does and do not care.
How do I get to "Download" folder from there?
I do not see it anywhere.

---

### Post by dddman on 2021-06-18
FileSystem>home/your user name/...

---

### Post by ajgreeny on 2021-06-18
> **anneranch said:**
> OK , I bypass "File manager" phony security by  command 
sudo nautilus 

That gets me to "snap" which I have no clue what it does and do not care.
How do I get to "Download" folder from there?
I do not see it anywhere.
You really should care about what you are doing, particularly when using **sudo** for anything!
And it what way is that "phony security"?

What do you need to use the ***"sudo nautilus"*** command for; what are you wanting to do?

---

### Post by dddman on 2021-06-18
@ajgreeny
Do you mean vs this:
[https://ubuntuhandbook.org/index.php/2018/02/open-as-admin-nautilus-file-browser/](https://ubuntuhandbook.org/index.php/2018/02/open-as-admin-nautilus-file-browser/)

---

### Post by ajgreeny on 2021-06-18
> **dddman said:**
> @ajgreeny
Do you mean vs this:
[https://ubuntuhandbook.org/index.php/2018/02/open-as-admin-nautilus-file-browser/](https://ubuntuhandbook.org/index.php/2018/02/open-as-admin-nautilus-file-browser/)
No, not specifically.

I was wondering what was meant by that "phony security" statement and I was also commenting on the "I don't care" attitude of the original poster.

While there may be sensible uses for a file-manager run as root, it is absolutely imperative that the user knows exactly what they are doing and why they need to do it.
Too many times in this forum we have seen users asking questions after doing something that was neither necessary nor appropriate for the problem they were trying to solve.

---

### Post by grahammechanical on 2021-06-18
The answer is to click on File System, then home, then on the folder with your user name, and then you will see the folders called Desktop, Documents, Downloads, Music, Pictures, Public, as well as Snap, and also Templates & Videos.

---

### Post by dragonfly41 on 2021-06-18
OP might find a two pane file manager useful to try out.
I use Krusader but there are several others.
They are similar to Total Commander in Windows.

---

### Post by grahammechanical on 2021-06-18
Nautilus is a two pane file manager and in the left pane it gives easy access to the default home/user folders. But when we load Nautilus using the sudo command it does not give easy access to those default home/user folders even though it still remains a two pane file manager. But the access is there.

I do not know the reasoning of the Gnome developers in making Nautilus work this way. Perhaps they think that a person running Nautilus using sudo needs to proceed especially carefully and determinedly.

Regards

---

### Post by Impavidus on 2021-06-19
Downloads is just a directory. You can navigate to it.

When you run a file manager with sudo, it's environment changes. The Downloads directory for the ordinary users is defined (usually as $HOME/Downloads), but that of the root user isn't. On the most recent Ubuntu versions, sudo also sets your home directory ($HOME). On older version only if specifically requested with the -H option. The home directory of your ordinary user is usually /home/username, that of the root user is /root. As root never uses a GUI session and never downloads anything, root doesn't need a Downloads directory.

As for "I don't care" attitudes, if you only care about the immediate solution of your problem, you won't learn about the background and won't learn to solve your problems on your own (or prevent problems). On this forum we don't normally give immediate solutions to problems, hoping the user will come back for as many new problems as possible. That's for commercial support. We try to educate the user so that some day the user won't come back with new questions, but with answers. That more interesting to us.

---

### Post by dragonfly41 on 2021-06-19
Just a added note on this ..
> [COLOR=#000000]Nautilus is a two pane file manager [/COLOR]
Nautilus is not quite the same as two pane file managers such as Krusader (my choice), Double Commander, Midnight Commander.
In Nautilus, clicking on a target (e.g. Downloads) in left navigation pane opens it in right pane.
But in the other managers a project folder can be fixed in right pane and the left pane can be used to navigate to target (to transfer content).

[P.S.] 
I must not forget the four pane manager.  [https://www.4pane.co.uk/](https://www.4pane.co.uk/)

And finally.. Krusader has an option .. Tools > Start Root Mode Krusader (Alt+Shift+K)

---

### Post by dddman on 2021-06-19
Hello people

I have returned from my quest and I bring "-H".  

sudo -H nautilus

That would be the correct way.

---

### Post by anneranch on 2021-06-19
> **dddman said:**
> FileSystem>home/your user name/...

OK, after "sudo nautilus" I get two pane display and on left I have "Filesystem root" (sic) then "home"  then user (?) / name and then I get to the "Download". 
Now the downloaded file is pretty small so I do not get any indication it was copied , but it did. SUCCESS

PS 
I  have made an error skipping your entry and reading all the social chat my post created first. 
Some factual, some entertaining. I find it puzzling why some folks are more worried 
about MY system security and miss to really answering the post question.
My next project is to write AI software "how did the answer  matched the question? "

---

### Post by dddman on 2021-06-19
[s]That's wrong, did you not read my post.  You can brick your machine without the -H.  Or don't you care.[/s]

---

### Post by ajgreeny on 2021-06-19
> **dddman said:**
> That's wrong, did you not read my post.  You can brick your machine without the -H.  Or don't you care.
If anneranch's machine is running 20.04 or later version of Ubuntu it is actually safe to use ***sudo nautilus*** and not bother with the additional ***-H*** in the command.

Prior to 20.04 (or maybe 19.10, I can't remember when) using ***sudo*** for a GUI application, particularly the file manager, could change ownership of files and folders in your home to root, completely removing your ability to login to the system as user.
Changes to the way the system uses ***sudo*** means that the danger of that happening has now gone so it should be safe as far as that problem is concerned.

However, if anneranch is not even aware of how to navigate to Downloads in the home folder after opening nautilus as root, I wonder if it is safe to be using the file manager as root at all, because it would be far too easy, if you're not totally sure what you're doing to completely kill the complete OS. 

Change ownership of home files and folders, can be easily put right if you know how.
If you inadvertently made such changes to files and folders in the root file system it would mean a reinstallation as ownership and permissions of root files and folders is extremely varied and can not be repaired with a simple command.  They are not all owned by root and some very specific permissions needs in order to work.

So, the point of all this, and what I meant by my comments> You really should care about what you are doing, particularly when using sudo for anything!
And it what way is that "phony security"?

What do you need to use the "sudo nautilus" command for; what are you wanting to do? 
was that if you do not already know the answers to the questions you asked, you certainly should not use command ***sudo nautilus*** as it will put you in a very dangerous position with the ability to kill your system with just a simple action.

---

### Post by dddman on 2021-06-19
Well nuts, I thought I found something.

Thanks

---

### Post by Impavidus on 2021-06-19
> **anneranch said:**
> I find it puzzling why some folks are more worried 
about MY system security and miss to really answering the post question.

Two selfish reasons:
1: Once your computer is hacked and turned into a bot, it will annoy all internet users, including us.
2: If you repeatedly break your Linux-based operating system, you might decide to tell other people how horrible it is. This discourages other people from using it, and the less people use Linux on the desktop, the less support software and hardware vendors will provide.

I guess you don't care about the other reasons we might have, but I've alluded to them in post #9.

---

### Post by tea for one on 2021-06-19
> **Impavidus said:**
> Two selfish reasons:
1: Once your computer is hacked and turned into a bot, it will annoy all internet users, including us.
2: If you repeatedly break your Linux-based operating system, you might decide to tell other people how horrible it is. This discourages other people from using it, and the less people use Linux on the desktop, the less support software and hardware vendors will provide.

I guess you don't care about the other reasons we might have, but I've alluded to them in post #9.

Yes, good observations - well made =d>

---

