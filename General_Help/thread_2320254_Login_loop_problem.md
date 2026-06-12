---
title: "Login loop problem"
date: 2016-04-12
forum: General Help
---

### Post by fbdonaldson on 2016-04-12
During my act of upgrading my desktop computer from Ubuntu 15.04 to 15.10 I, following advice from this location, went into the System's software sources, PPA tab and disabled some items.

Then, before I installed 15.10, I rebooted the computer to make for a clean install of 15.10.
 
So, what happens but login loop!  Undaunted, I went ahead and installed 15.10 via the terminal hoping that it would sort the issue; but no luck there. 

I'm sure it is the PPA editing that is the problem but I don't know how to approach it without the graphics in operation.
 
This has never happened in previous upgrades

---

### Post by Impavidus on 2016-04-12
The most common cause for a login loop is that one or both of the following files have become root-owned. Login using the console (ctrl-alt-F2) end check with```
ls -l .Xauthority .ICEauthority
```Also make your they are writable by the owner. If they are root-owned, the GUI crashes as soon as it is started because it has no write permissions there. You can simply delete the files. They will be recreated on the next login attempt.```
rm .Xauthority
rm .ICEauthority
```You can also change ownership to yourself.```
sudo chown your_user_name:your_user_name .Xautority
sudo chown your_user_name:your_user_name .ICEauthority
```The problem may have been caused by running GUI applications as root without a proper root environment, in other words, using sudo the wrong way.

---

### Post by fbdonaldson on 2016-04-12
Getting the "cannot access Xauthority no such file or directory."

---

### Post by howefield on 2016-04-12
> **fbdonaldson said:**
> Getting the "cannot access Xauthority no such file or directory."

Did you note the period in the filenames ?

Usually best to post the entire command used along with the output (between code tags) so others can see exactly what you have done.

---

### Post by ajgreeny on 2016-04-12
Looks like you may have missed the . at the start of the file names, ie **.Xauthority** which is very important, and makes the files hidden (unless you use Ctrl+H in your file-manager).

Check that and try again.

Just out of interest have you ever used a GUI application with sudo in order to open it with root permissions, eg **sudo nautilus**?

That can cause the ownership of files and folders in your home to move to root instead of you as user.  Use **gksudo nautilus** or **sudo -H nautilus** instead and you should be OK in future.

EDIT:
ninja'd by howefield; again!

---

### Post by fbdonaldson on 2016-04-12
Placed it in Placed it in wexactly as you wrote.
Including the dots.
As for the nautilus question : never used nautilus: still thinkthe problem is the PPA edit that I did whilst still in 15.04

---

### Post by howefield on 2016-04-12
> **fbdonaldson said:**
> ..still thinkthe problem is the PPA edit that I did whilst still in 15.04

You can enable the ppa that you disabled if you think that will help although disabling third party ppas is the right thing to do when upgrading, (I might be wrong but I think that the upgrade process now does that automatically). I'm not sure that telling apt to ignore a particular ppa would lead to a login loop.. but hey, stranger things have happened.

All disabling a ppa through the Software & Updates application does is put a # sign in front of the relevant sources line, presumably you can get to a command line if you are entering the above commands so try..

```
ls /etc/apt/sources.list.d/
```

then open the relevant list file and remove the # signs as required.

```
sudo nano /etc/apt/sources.list.d/ppafilename
```

Ctrl + o, then enter, then Ctrl + x to save and close the editor.

---

### Post by fbdonaldson on 2016-04-12
When I try the 'rm' command on ICEauthority, I get the "permission denied" outcome.

---

### Post by Impavidus on 2016-04-12
Regardless of whether removing .ICEauthority would solve your problem, you shouldn't get a permission denied error. What do you get from```
cd ~
pwd
ls -ld .Xauthority .ICEauthority .
```(Note the dot at the end)

---

### Post by fbdonaldson on 2016-04-12
BTW:I am communicating via my tablet.

The result for the above is:  cannot access .Xauthority:No such file or directory 
etc off screen? -xr-xr-x 37 USER USER  4096 Apr 12 21:32 .
etc off screen ------- 1 USER USER 159124 Apr  2 21:17 .ICEauthority

---

### Post by fbdonaldson on 2016-04-13
ALSO: Connection to the internet is as per usual.

When rebooting I get just  a fleeting glimse of the main Ubuntu logo before it reverts to the second rate display.

---

### Post by Impavidus on 2016-04-13
> **fbdonaldson said:**
> BTW:I am communicating via my tablet.

The result for the above is:  cannot access .Xauthority:No such file or directory 
etc off screen? **[COLOR=red]-r-xr-x[/COLOR]** 37 USER USER  4096 Apr 12 21:32 .
etc off screen ------- 1 USER USER 159124 Apr  2 21:17 .ICEauthority

Edit: *Just to check, first try running*```
stat . .ICEauthority
```*That should give all important output on your screen.*

The output is incomplete, but it seems that you don't have complete access to your own home directory. Do you have any idea what might have caused that? You are the owner of .ICEauthority, so that's OK, but I can't see whether you have read/write access there. Try fixing this with```
chmod 755 ~
chmod 600 ~/.ICEauthority
```

---

### Post by fbdonaldson on 2016-04-13
Yes it gave a full screen of info: blocks Inode etc.

The answer to the query is incompetence, sadly and before I move onto the next instruction, I need to know how to make my tilde go centre and not upperzone on my qwerty board. Is there a code or something?

---

### Post by fbdonaldson on 2016-04-13
I should explain that my computer has a SSD for the root directory and HD for data etc. Expect that the 15.10 install worked all that out. Previous installs
all went well.

---

### Post by Impavidus on 2016-04-13
> **fbdonaldson said:**
> Yes it gave a full screen of info: blocks Inode etc.Yes, so what information did it give you? Most importantly, what were the permissions (access flags) for the file and directory?
> The answer to the query is incompetence, sadly and before I move onto the next instruction, I need to know how to make my tilde go centre and not upperzone on my qwerty board. Is there a code or something?The tildes aren't that important. If you're in your home directory you can skip the ~/ and still get the same result. Just hitting the tilde key (that is, shift+`) should work. Whether you get one in the centre or higher depends on the font.

---

### Post by fbdonaldson on 2016-04-14
Hello again. I have been trying to attach a screen photo of my results to your command suggestion: stat .........

 etc. But it is very difficult as this paintbrush style app insists on an URL to the file for upload.

My tablet is android operated and it took the photo. Any suggestions to enable us to go forward?

Also, thanks for your perservarance with me.

---

### Post by Impavidus on 2016-04-14
When you reply, you can click "Manage attachments" -> "Add files" and upload the image. Alternatively, upload to some external image sharing service and post a link or copy the text manually (just the important bits). Normally it should be possible to save the output of commands to a file and send that somewhere, but I think that may be broken on your system.

---

### Post by Jasper_HD on 2016-04-14
I also had this problem (could login as guest, not my regular sudoer user which just looped) - I realised the problem was connected with me encrypting my home directory.

Here's how I fixed it (Ubuntu 15.10):

[LIST]
[*]At the login screen I switched to the terminal (CTRL + ALT + F1) (BTW: CTRL + ALT + F6 takes you back)
[*]I  went down the avenue of trying to manually decrypt the home directory  as all I could see was (Access-Your-Private-Data.desktop) and a  readme.txt file.
[*]Using the command (ecryptfs-mount-private) I realised ecryptfs wasn't installed
[*]I suspected some libraries I installed to try and see a Windows network share, so I found recently packages installed ([http://askubuntu.com/questions/17012...-packages)sudo]("http://askubuntu.com/questions/17012/is-it-possible-to-get-a-list-of-most-recently-installed-packages%29sudo") awk '$3~/^install$/ {print $4;}' /var/log/dpkg.log
[*]I removed those packages - [http://askubuntu.com/questions/15194...move-a-package]("http://askubuntu.com/questions/151941/how-can-you-completely-remove-a-package")
[*]I then created a new user via the terminal: [http://mixeduperic.com/ubuntu/how-to...mand-line.html]("http://mixeduperic.com/ubuntu/how-to-add-a-new-user-in-ubuntu-using-the-command-line.html")
[*]And added them to the root/sudo users: [http://mixeduperic.com/ubuntu/how-to...on-ubuntu.html]("http://mixeduperic.com/ubuntu/how-to-setup-a-user-or-group-with-sudo-privileges-on-ubuntu.html")
[*]I then rebooted and successfully logged into the GUI with the new root-level user.
[*]This enabled me to install the ecrypt library: *[COLOR=blue]sudo apt-get install ecryptfs-utils ([http://linuxpoison.blogspot.co.uk/20...tographic.html]("http://linuxpoison.blogspot.co.uk/2010/10/how-to-use-ecryptfs-cryptographic.html"))[/COLOR]*
[*]One reboot later and I could login to the GUI with my original user
[/LIST]

---

### Post by fbdonaldson on 2016-04-14
[USER]-MS-7721:~$ stat . .ICEauthority 
File: (square).(square)
Size: 4096   Blocks: 8  IO Block 4096 directory
Device: 802h/2050d Inode 3157359  Links: 37
Access: (0755/drwxr-xr-x) Uid: (1000/  [USER]) Gid: (same)
Access: 2016  etc
Modify: 2016 etc
?ange: 2016 etc
_irth: -
File:  (square).ICEauthority(square)
Size: 159124  Blocks: 320 IO Block: regular file
Device: 802h/2050d Inode: 3157266   Links: 1
Access: (0600/-rw-------) Uid: (etc)  Gid: (etc)
Access: 2016 (etc)
Modify: 2016 (etc)
etc
etc

---

### Post by Impavidus on 2016-04-15
That looks OK. The user ID of both was the same, right?

Have you tried logging in again? If you still can't, something more complex is going on. Have you tried a guest session?

---

### Post by fbdonaldson on 2016-04-15
Funny you should say that.

I just powered it up after work this evening and wasn't even going to bother putting the pasword in intending to go straight to the Terminal.
However I did and voila! it went into the 15.10 display of which I hadn't seen before.

l must have got some of your instructions correct.

Anyway, thank you so much for you patience.


Actually, I am not quite out of the woods yet as I have some missing files to chase up but that can be for further info gathering onmy part.

So I expect that this thread can now end.

Cheers
Barry

---

### Post by mörgæs on 2016-04-15
Good, then please go to Thread Tools and mark it solved.

---

