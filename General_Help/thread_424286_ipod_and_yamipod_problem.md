---
title: "ipod and yamipod problem"
date: 2007-04-26
forum: General Help
---

### Post by curtk69 on 2007-04-26
wasnt getting any replies inother forum so

 ipod and yamipod
hey dudes i am a newbie to ubuntu/linux
i have 2 problems

one, my ipod will play in ubuntu but the files/folders are totally differently organized at what seems random order and no name folders listed as 1-49.
my previous playlists are nowhere to be seen in the music folder, there are just 49 folders containing random songs between 18 and 24 about.

how do i see my playlists?

second, i itried installing yamipod. it opens my ipod and shows the songs but i get an error saying no audio will be available till i in stall a certain file that came with yamipod.
but when i try to installl said file i am told i am not the owner/dont have permission to write to the usr/lib folder.

so how do i get permission?

---

### Post by roachk71 on 2007-04-26
Not absolutely sure is this will work the way it should, but try installing the hfsplus and hfstools packages from Synaptic or Adept. You need support for Apple's HFS filesystem to do anything useful with an iPod.

---

### Post by curtk69 on 2007-04-26
i a linux newbie so i need specific instructions how to do that? thanks

---

### Post by MagisterJoe on 2007-04-26
> **curtk69 said:**
> wasnt getting any replies inother forum so

 ipod and yamipod
hey dudes i am a newbie to ubuntu/linux
i have 2 problems

one, my ipod will play in ubuntu but the files/folders are totally differently organized at what seems random order and no name folders listed as 1-49.
my previous playlists are nowhere to be seen in the music folder, there are just 49 folders containing random songs between 18 and 24 about.

how do i see my playlists?

I believe this is the result of the iPod's obfuscation scheme.  iTunes knows how to read a database that tells it where each track is located, but to make track sharing between users harder, each file as a randomized name and is put in a randomized folder.  If you just browse the file tree, you'll never find them.

When I plug my iPod in, I have exactly the same file structure.  Your playlists are actually contained in a file called **iTunesplaylists** in the iTunes directory, but it is similarly obfuscated.

> **curtk69 said:**
> second, i itried installing yamipod. it opens my ipod and shows the songs but i get an error saying no audio will be available till i in stall a certain file that came with yamipod.
but when i try to installl said file i am told i am not the owner/dont have permission to write to the usr/lib folder.

so how do i get permission?

I think that what you are missing is root permission to install the file.  Depending on the distro (are you using Ubuntu?) you can get permissions by using the 'sudo' command or by using the 'su' command.  Here's an example:

[INDENT]
~$ sudo COMMAND
Password: (*type your password*)
[/INDENT]

Then, type your password, and COMMAND will be executed with root privileges.  Alternatively, if you are not using Ubuntu, you may need to:

[INDENT]
~$ su
Password: (*type ROOT password*)
root@system:~$COMMAND
root@system:~$exit
~$[/INDENT]

This will also execute the command with root privileges.  Just make sure you close the terminal or type 'exit' so that you don't continue to execute commands as root.  Otherwise, you might accidentally destroy something important.

---

### Post by roachk71 on 2007-04-26
In Ubuntu (GNOME) or Xubuntu (XFCE), you'll find Synaptic Package Manager in your System Menu, and
in Kubuntu (KDE), K Menu-->System-->Adept Manager.

Synaptic works somewhat in an easier manner; simply use the search function (make sure the search type is only by name!) to find the packages, then when the results are loaded, click on the small icon next to each package and select Install from the drop-down menu. Now click the Apply button. Once this is finished, close Synaptic and restart your system.

In Adept, there's an automatic search pane; just type the first few characters of the package name(s) and it begins the search for you. Now you'll have to wait until all the results have been scanned for (you'll see text in the rightmost listing pane.) In Adept's case, click on the package names themselves, and it'll drop down. Click the "Request Install" buttons for each package, then click the "Apply Changes" button. After installation, close Adept and reboot your machine.

Now, you shouldn't have to do anything to load the driver modules, since they'll automatically be loaded at boot time.

---

### Post by curtk69 on 2007-04-27
curt@curt-ubuntu:~$ su
Password:
su: Authentication failure
Sorry.
curt@curt-ubuntu:~$

thats what i get when i open a konsole window and type in the su command and enter my password?  wtf?

---

### Post by curtk69 on 2007-04-27
and when i search for the package in synaptic  i get the package listed in the left hand pane but no icon or anything to click on?

---

### Post by roachk71 on 2007-04-27
Try using sudo -s -H instead, with your user password. The root account is disabled by default in Ubuntu, so it doesn't yet have a password.

If, on the other hand, you just need to run a single command, just use sudo followed by the command to run.

Examples:
```
sudo -s -H
command
```

```
sudo command
```

the 'su' command needs the superuser (root) password, so it can't be used until you've defined one. If you'd like to do this, issue the following:

```
sudo -s -H
passwd root
```

CAUTION: For security, you'll be typing any passwords in the console blind.

---

### Post by curtk69 on 2007-04-27
i think i already have a password system since i have to log on with a password and when i do try to change certain things i am asked for my passwrd?

---

### Post by roachk71 on 2007-04-27
For better security, the short answer is yes. Unlike Windows XP, in Ubuntu you need either a root password or (in most cases) your user password to make changes to the system configuration.

This is part of the operating system's philosophy; it keeps anybody except the owner or administrator from mucking up your system. But at least you don't have to deal with an alert each time, like in Vista... :KS

The only time this isn't the case is when you're using the sudo -s -H command I explained earlier. In that case, you can issue as many commands as superuser as you like, until the exit command is used.

Oh, and I'd forgotten to mention: the sudo command has a grace period, so you don't have to type your password each time it's used.

---

