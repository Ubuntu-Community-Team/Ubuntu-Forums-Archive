---
title: "Customizing 20.04 lightdm guest session - unexpected login loop"
date: 2020-08-13
forum: General Help
---

### Post by kolinab on 2020-08-13
**Summary**

I  have 8 Ubuntu 20.04 systems running in a public setting with the  guest  session enabled. I have customized them using the guide at  [https://help.ubuntu.com/community/CustomizeGuestSession](https://help.ubuntu.com/community/CustomizeGuestSession).

This  has been working great. Recently I added a folder in the   /home/librarian/Desktop folder linked to the guest-session. The   result was a login loop that prevented me from logging into the guest   session.

I have solved the problem for now by  removing any *folders* (files seem to be OK) from:

/home/librarian/Desktop

**Goal** a working guest session with 

[LIST]
[*]customized application shortcuts 
[*]a custom scaled background image 
[*]custom bookmarks in Firefox and Chrome 
[*](a few folders of files on the desktop) - not yet working, haven't worked on this yet 
[/LIST]

**Setup** These are the steps I used:

[LIST]
[*]clean install of 20.04.01 to the whole disk 
[*]admin and only user is 'librarian' in /home/librarian 
[/LIST]

```
#apply updates
sudo apt update && sudo apt upgrade -y

#install lightdm to enable guest session
#install gnome-tweaks to adjust desktop background scaling
sudo apt install lightdm gnome-tweaks -y

#enable guest session
sudo sh -c 'printf "[Seat:*]\nallow-guest=true\n" > /etc/lightdm/lightdm.conf.d/40-enable-guest.conf'

#turn off initial setup screens for guest user
sudo apt purge gnome-initial-setup -y

#download and install google-chrome-stable
wget [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)
sudo apt install ./google-chrome-stable_current_amd64.deb

#symlink /etc/guest-session/skel to /home/librarian
sudo ln -s /home/librarian /etc/guest-session/skel
```

 Next I:

[LIST]
[*]set a custom background screen in the GUI with an image from /home/librarian/Downloads and scale it using gnome-tweaks 
[*]create three bookmarks in the bookmarks bar in Firefox and Chrome, and  set a few browser preferences. This works great, no issues. 
[*]prevent Chrome from asking for keyring on login by following the instructions here: [https://ubuntuforums.org/showthread.php?t=2377036&p=13708937#post13708937](https://ubuntuforums.org/showthread.php?t=2377036&p=13708937#post13708937) 
[/LIST]
 
**Problem**

This week I added some files to /home/librarian/Desktop,  which I hoped would appear on the desktop in the guest session. **Then  when I attempt to log in to the guest session, the login fails after a  long delay and brings me back to the lightdm login screen.**

It  appears that a guest session is running, as there is a new entry in the  chooser for 'Guest,' but I am unable to access a desktop. Clicking on  'Guest' prompts me for a password, which has not been set. Another  'Guest' entry in the list appears in the greeter each time I attempt to log in. When I  log in as admin user, I see folders left behind that have been created  for each session I attempted in /tmp/guest-XXXXXX.

**Other Solutions I tried**

I also tried the steps for customization at [https://ubuntuforums.org/showthread.php?t=1566078&p=11717490#post11717490](https://ubuntuforums.org/showthread.php?t=1566078&p=11717490#post11717490) (simplified below)

 1. Create the directory /etc/guest-session/skel
 2. Start a guest session
 3. Make changes and customization to the guest session using whatever  tools/utilities you wish
 4. Switch to admin account, cd to /tmp, and find the temporary guest home directory (guest-XXXXX)
 5.  Copy the files in the temporary guest home directory to  /etc/guest-session/skel using the command: ```
sudo cp -rT /tmp/guest-XXXXX  /etc/guest-session/skel
```

This works. Unfortunately using this method:

[LIST]
[*]Custom desktop background selected using the GUI doesn't stick (I tried setting choosing an image from /home/Downloads and /usr/share/backgrounds) 
[*]Firefox shows an error preventing bookmark functionality 
[/LIST]
  
I also tried/checked:
 
[LIST]
[*]deleting the symbolic link in etc/guest-session/skel and copying the actual files from /home/librarian to /etc/guest-session/skel (no effect on boot loop) 
[*]deleting /etc/.pwd.lock (no effect) 
[*]deleting .XAuthority (no effect) 
[*]/etc/guest-session/prefs.sh does not exist 
[*]deleting all files and folders in /etc/guest-session/skel EXCEPT .local  and .config (I wanted the settings inside) works. This, however, causes strange  behaviour. Logging in to the guest session this way it appears the  temporary guest files that should be in /tmp/guest-XXXXXX all show up on the guest-session desktop. I might test this  again and update. 
[/LIST]
 
**Next I will work on**:
[LIST]
[*]different ways of adding folders or shortcuts that would be visible on the desktop, so guests can access some 'read only' files (perhaps on a network location so the files could be updated centrally) 
[*]creating an actual 'guest-prefs' user instead of linking from my administrator account (I am not sure if linking from my admin user causes problems or not) 
[*]automating this setup so I can plug in a USB stick of files (or better yet, access a network location) and update the guest session settings with a single script 
[*]investigate /usr/sbin/guest-account.sh and how it works 
[*]setting an idle user logout time, so unattended systems logged into the guest-session logout after x minutes of inactivity 
[/LIST]

[EDIT: marking this as solved -- I have solved the boot loop and will work on more functionality. Many thanks to those who contributed to the many guides and howtos on this topic, especially the maintainer of ["]https://help.ubuntu.com/community/CustomizeGuestSession]("https://help.ubuntu.com/community/CustomizeGuestSession.)

---

