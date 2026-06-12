---
title: "I am idiot! (Sound/Groups/Installs/etc.)"
date: 2007-12-01
forum: General Help
---

### Post by Choobie on 2007-12-01
Okay, this is day two of dabbling into Linux. I have already managed to whipe my hard drive clean (instead of just installing into a partition, no big deal I have a backup, but I don't want to put Vista back on if I can help it (actually I can't, I don't have a vista boot or restore cd :P))

So lets get going then :D I am running on Ubuntu 7.10 Gutsy Gibbon, Desktop i386

I think I screwed up the groups too. I was looking around for a fix to my sound problem and found one site that suggested I was removed from the Audio group or something and couldn't access the sound card. When I tried inputting the commands it gave me, I got a bunch of Permission Denied notices. Fine. I tried another another command (mkdir I think) and got another permission denied notice. Great. I went to System -> Administration planning on looking into the Users and Groups GUI, but its not there, In fact there are only a few items in the Administration menu, whereas before there had been like 20. No Synaptic Package Manager, no Restricted Device Manager etc.

Crap. I have no idea what is going on with this, but it looks like I lost most of my administrative privileges. Any help here would be appreciated.

Next is my sound card. I get the "No volume control GStreamer plugins and/or devices found." error when I try and edit the volume. I saw a ton of other posts on this forum about it, looked through a bunch of them, but still haven't found anything that really helps me. Keep in mind that I am stupid though. I looked into the GStreamer stuff a little, but I don't really understand it. What plugins do I need to install? Do I even know if my sound card's driver is working? I think this is the thing I need: [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel) because it is part of the ICH7 Chipset, here is the output from lspci:

> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Of course, I have no idea what exactly I am doing. Trying to follow the install directions on that page fails because I don't have permission to do "mkdir alsa" and trying to do it through the GUI just leaves the "Create Directory" button grayed out.

And like I have said before, I am pretty clueless about how everything works on Ubuntu right now. I can usually follow Terminal commands pretty wel, but I am still pretty much a complete noobie](*,) 

Edit: Another question: How do I know if the rest of my drivers are working correctly? In windows everything was under Device Manager but I haven't seen anything like that so far.

Edit: Another thing I noticed is that Applications -> Add/Remove Applications is missing. I can't install anything, even through the Terminal. Typing "sudo apt-get install gparted" for example does nothing.

---

### Post by jonnymccullagh on 2007-12-01
There are a lot of questions in there but for the first one.
That other website probably suggested editting files and creating new directories but to do this in Ubuntu outside your own home directory you will need to take this action sudoing (pretending to be) the root (super administrator) user.

to do so at the command line you will need to type:
sudo mkdir /opt/some_directory_name
instead of just:
mkdir /opt/some_directory_name

When you installed Ubuntu you defined the first user - who automatically got the rights to perform 'sudo' commands. So you should probably try logging in as that user. It sounds like you may have created another user and are now logging in as that user. Unfortunately you have not given that second user the rights to do 'sudo'. You should be able to change this by logging back in as the first user and visiting Ayatem -> Administration -> Users and Groups. Under the properties of the second user find the permissions tab and tick the box which allows them to adminster the system.

You may not like the sudo stuff but it does have good benefits.

Hope this helps you get started solving your problems,
jonny

---

### Post by Choobie on 2007-12-01
Nah, I only created one user "choobie" and did a bunch of stuff with sudo and installed some applications and stuff as "choobie" but I can't do that anymore.

This will probably catch some backlash, but other than re-installing I don't see any other way: How do I log in as root so that I can at least create a new user with sudo privileges, or  fix my current user's privileges?

---

### Post by jonnymccullagh on 2007-12-01
I'm not sure what you can do without being able to sudo for any user and I don't know how you managed to do that ! 
You could take a look at the /etc/passwd file with:
more /etc/passwd
for users with an id over 1000 ?
and 
more /etc/group
to see if choobie is a member of the adm group.
But in any case if you can't sudo anything  then you can't log in as root and other than re-installing you would probably have to run the LiveCD again and manually amend the files above to give yourself the necessary rights?

---

### Post by Choobie on 2007-12-02
> But in any case if you can't sudo anything then you can't log in as root and other than re-installing you would probably have to run the LiveCD again and manually amend the files above to give yourself the necessary rights?

Yeah thats pretty much what I did. Running on a clean install of Ubuntu now. I'm going to start over and avoid user group modifying. Also created a backup user off the bat with admin privileges. Hopefully things will go better this time around.

---

