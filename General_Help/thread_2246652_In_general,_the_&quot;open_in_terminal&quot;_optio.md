---
title: "In general, the &quot;open in terminal&quot; option from the right click menu has quit working."
date: 2014-10-02
forum: General Help
---

### Post by landstander on 2014-10-02
**_Important Note:_**
I have reposted this question as a new thread because the original thread had a title that suggested this problem was specific to a file manager called Nemo. However in the testing done in the previous thread it was discovered that this issue was a system wide problem and most likely had nothing to do with the installed file manager. The title of the previous thread was only attracting the attention of people who could help with Nemo specific issues. Therefor it was necessary to repost this question as a new thread without the keyword Nemo in the title. For reference here is a link to that previous thread:
[http://ubuntuforums.org/showthread.php?t=2246139]("http://ubuntuforums.org/showthread.php?t=2246139")

**System Specs:**
OS: Lubuntu 14.04
Desktop: Lubuntu
Window Manager: Openbox 3.5.2
Compositor: Compton
File Manager: Nemo 2.2.4

**Description of problem:**
From any right click menu that gives an "open in terminal" option (including right clicking on the desktop), nothing happens at all if that option is selected.

**Things I have tried:**
**1.)** I have searched through both the gconf-editor and the dconf-editor and both editors agree in terms of there respective settings for any terminal command strings.
**2.)** I have also checked and searched through the gsettings command for items related to a terminal, and nothing seems out of place here as far as I'm able to understand it so far.
**3.)** I also did a strace of the currently installed file manager to see if I could get some information about what is happening during a right click menu selection of the "open in terminal" option and I couldn't understand the output from strace and couldn't find any reference to any "open in terminal" command listed in that output.

**Questions and requests:**
1.) Is there a setting someplace that I am missing for how the right click menu opens a terminal?
2.) Could you please offer a method for probing this issue a little further than I have?
3.) Please let me know if there is any output from any commands that you wish to see.

Thanks.

**Final note:**
I've searched for a solution both on the web and in these forums and this returned no results for a Lubuntu 14.04 specific case. The cases I did find were related to Fedora (which had packages Lubuntu doesn't have or need), and Arch which was unfortunately out of context for the issue I've posted here. I have also used the "Check if Already Posted" button next to the subject line which only returned my previous post which had an incorrect title and was misleading people who might be able to help. It is for these reasons that I'm hoping this post is unique and is not a repost that has already been answered someplace else.

---

### Post by tgalati4 on 2014-10-02
Don't know how it is done in Openbox, but in Linux Mint MATE, based on gnome2, those menu entries are defined in /usr/share/application-name and ~/.local/share/application-name and is controlled by the MATE window manager.  In Openbox it is probably completely different or Openbox does not have a way to add to the Right-Click (context menu).  An alternative is to install *guake* and use the pull down terminal or hot-key to bring up a terminal.

Look in /usr/share/nemo and ~/.local/share/application/nemo for any xml or menu files.

My guess is that building, installing, and removing different versions of Nemo has caused the configuration files to get messed up, thus no Right-Click "Open in Terminal".

---

### Post by landstander on 2014-10-03
Just a quick note to make sure its clear,

This isn't just happening in Nemo. It also happens outside of Nemo (e.g. when Nemo isn't running) if I right click on the desktop there is an "open in terminal" in that menu as well and this option also does not work. If someone could clarify if that right click menu on the desktop is also being controlled by whatever file manager the operating system is currently using as its default that might help clear up one part of my confusion.

@tgalati4
Thanks for the heads up and extra info. I will look into those configuration files and into some Openbox forums to see if I can find a solution there.

Just a quick note on the configuration files mentioned in the last two posts.

/usr/share/nemo didn't have anything of use in it, there was a /usr/share/nemo/actions folder which I assume is working sort of like a nautilus scripts folder. (Worse case scenario maybe I could write a script that would open the current folder in a terminal if this actions folder is for what I think it might be for.)

there were no xml files or menu files located in ~/.local/share/nemo and there was no nemo folder located in ~/.local/share/applications nor was there any xml files listed there, only *.desktop files.

---

### Post by tgalati4 on 2014-10-03
Here are a few more things to try:

[http://ubuntuforums.org/showthread.php?t=2197247](http://ubuntuforums.org/showthread.php?t=2197247)

[http://pclosmag.com/html/Issues/201108/page10.html](http://pclosmag.com/html/Issues/201108/page10.html)

Half the battle is just finding where those pesky menu.xml files are stored!

---

### Post by landstander on 2014-10-03
[Update:]
I haven't been able to locate or find any configuration files for Nemo that will let a user configure or change its right click menu settings. All of the options to get to Desktop Preferences (such as from launching "pcmanfm --desktop-pref) seem to give an error message of "Desktop manager is not active." and searching for this error message opens up too many solutions that don't seem to address my specific situation of having installed Lubuntu (as an option in the login screen) ontop of an Ubuntu with Gnome desktop distribution.

However the default file manager for Lubuntu seems to have all the functions that nautilus and Nemo have (dual pane, open current folder in terminal, etc.) so I might try and get rid of Nemo all together and try and reconfigure Lubuntu to use its preferred default file manager of pcmanfm to see if this fixes the problems opening the desktop in a terminal or the same problem with opening any directory in a terminal via the file manager.

**_[SOLVED:]_**... sort of?

At some point Nemo quit working as expected inside a Lubuntu session. Where here, Lubuntu was added as an extra login option under Ubuntu 14.04 (where Ubuntu was originally installed with the Gnome3 desktop as its default login session). As such I opted to reconfigure the Lubuntu session to use its preferred default file manager PCManFM. After doing that everything seems to be working as it should now. The right click menu option to open the desktop in a terminal works from the desktop and the right click menu inside the PCManFM file manager works to open any directory in a terminal as well.

If you replaced the default file manager in Lubuntu with Nemo then here are the
**_Steps to set PCManFM as the default file manager_**:
**_1.)_** This step assumes that you have the PCManFM file manager installed as it should be installed by default if you installed a Lubuntu desktop login option. After logging into the Lubuntu desktop, open the lxpanel's launcher menu bar (equivalent to the start menu in windows for users familiar with that OS) then goto [Preferences] --> [Default applications for LXSession] --> on the left pane [Launching applications] --> in the right pane [File Manager], and choose from this drop down menu --> [File Manager PCManFM].
**_2.)_** Logout of the session, then login again (this will reload all the associated window managers, file managers, and everything else all at once).
**_3.)_** The system should now have the pcmanfm file manager as its default file manager.

**_To test this_** and make sure it's working correctly just do something that triggers the operating system to open whatever file manager is set as its default. I'm not sure if this is the same for everyone or just something I configured along the way somewhere and I'm not sure how to find out, but if I download a pdf file in firefox it will automatically open the directory it was downloaded to in the file manager on my system. When I did this it opened PCManFM, which tells me it has been successfully installed as the default file manager.

If you were experiencing this same problem and were hoping to get Nemo's "open in terminal" function working under Lubuntu I apologize that I wasn't able to figure this out. My best guess is that it was some kind of Catch22 situation where I couldn't change the menu unless I had PCManFM desktop preferences daemon running and I couldn't have that running unless PCManFM was set as default, but since Nemo was needed as default to use its right click Menu... *shrug* there's probably a long convoluted procedure to get this to work involving going back and forth between setting each file manager as default to set appropriate settings until this is straightened out, but since PCManFM seems to work well enough for me I'm calling it quits on troubleshooting this any further.

I hope this was in some way useful to some one out there, but I realize that it probably wasn't, and I guess I'll mark this thread as solved even though it sort of wasn't solved for finding and configuring Nemo to work correctly. I wish there was an option to mark a thread as a workaround instead of solved.

---

### Post by mariofilippa on 2015-03-25
> **landstander said:**
> I hope this was in some way useful to some one out there, but I realize that it probably wasn't

Cheer up! It did solve MY problem (pcmanfm not responding because I had changed the default file manager). So THANK YOU!

---

