---
title: "Nemo File Manager: right click context menu &quot;open in terminal&quot; has quit working."
date: 2014-09-28
forum: General Help
---

### Post by landstander on 2014-09-28
**_System Specs:_**
**OS:** Lubuntu 14.04
**Desktop:** Lubuntu
**Window Manager:** Openbox 3.5.2
**Compositor:** Compton
**File Manager:** Nemo 2.2.4

**_Description of problem:_**
When the Nemo file manager is open, if the user right clicks in an empy unselected area of the window, an option to "Open in terminal" appears and when this option is selected, nothing happens at all. If Nemo is run from the terminal, there are also no error messages given in that terminal when selecting the "open in terminal" option from the right click menu inside Nemo's main file window pane.

**_Things I have tried:_**
1.) I have searched through both the gconf-editor and the dconf-editor and both editors agree in terms of there respective settings for both Nemo and or any terminal command strings.
2.) I have also checked and searched through the gsettings command for items related to either Nemo or a terminal, and nothing seems out of place here either.
**Note:** If any additional or more detailed output is required for the stated things I have tried, please reference a command that gives the required output for convenience and clarity for those following this thread.

**_Questions and requests:_**
1.) Is there a setting someplace that I am missing for how Nemo opens an external terminal?
2.) Could you please offer a method for probing this issue a little further than I have?

Thanks.

**_Final note:_**
I've searched for a solution both on the web and in these forums and this returned no results for a Lubuntu 14.04 / Nemo specific case. The cases I did find were related to Fedora (which had packages Lubuntu doesn't have or need), and Arch which was unfortunately out of context for the issue posted here. I have also used the "Check if Already Posted" button next to the subject line which returned no results at all. It is for these reasons that I'm hoping this post is unique and is not a repost that has already been answered someplace else.

---

### Post by ibjsb4 on 2014-09-28
I run a gnome 14.04 session that has openbox 3.5.2 and nemo 1.8.4 and it does work like you want 2.2.4 to work.  Maybe this is a bug or just no longer available in 2.2.4.  Where did you download nemo from, 2.2.4 it is not offered in the repositories.  I could load it just to verify this behavior.

---

### Post by landstander on 2014-09-29
I forgot to include some history and important information in my original post that could make a difference in how the problem is reproduced... if it can even be reproduced.

The original distribution I had installed was Ubuntu 14.04 with the Gnome3 desktop. When the Gnome team decided to remove important and useful features from Nautilus (this in combination with some system resource issues my computer was having) I decided it was important to install a Lubuntu desktop to restore some system resources and to install Nemo to restore the functions that the Gnome3 team removed from Nautilus.

Since I was running a Lubuntu environment it didn't make sense to keep using the gnome-terminal as the default terminal emulator, so I switched the default terminal emulator to lxterminal via the gconf-editor and the dconf-editor. I also checked if this was reflected by the gsettings command (see: man gsettings) and it was, so there seems to be no problem there.

One of the other reasons I moved away from Gnome3 was that it appeared as if the Gnome team removed the ability to have transparency in the gnome-terminal. So I found a supposedly light weight compositor called compton that allowed the system to have transparency in all inactive windows and in lxterminal which was good enough for what was needed.

Everything appeared to be working fine for a while and I was initially able to use the right click menu to open a terminal on any folder in Nemo, but after some time (I suppose this might be due to an update, but could also be due to something I set incorrectly or removed by mistake via either gconf-editor, dconf-editor, or the gsettings command) the ability to "open in terminal" via the right click menu in Nemo quite working. It is difficult to tell which of these issues might have been the culprit since its unclear when this functionality stopped working.

**@ ibjsb4:**
To answer your qustion, Nemo 2.2.4 was installed via the following PPA:
[http://ppa.launchpad.net/webupd8team/nemo/ubuntu](http://ppa.launchpad.net/webupd8team/nemo/ubuntu) trusty main
I saw no other way to install Nemo since it wasn't showing in the default repositories at the time it was installed.

In synaptic I can't do a "force version" on Nemo itself. If I select the option to do so, nothing happens. However I can downgrade some of the other packages Nemo depends on but this breaks Nemo itself. If an attempt at uninstalling Nemo is made then wont this result in a system that has no file management and wouldn't this result in an unstable system? In other words, how can Nemo be downgraded safely to v1.8.4 to test if it was the upgrade that broke it?

If the function in question was removed from Nemo 2.2.4 then this will be an issue that needs to be raised with the developers since the option to select "open in terminal" is still present in the right click menu. It is not uncommon for developers to overlook this type of thing when removing functionality, but I was hoping Nemo wouldn't go in this direction. 

**Note:**
The embedded terminal in Nemo isn't appropriate in my case since I need the ability to see more output than can be displayed in the small area provided for the embedded terminal.

---

### Post by ibjsb4 on 2014-09-29
Ok, I tried to install 2.2.4 on both Fallback (12.04) and Flashback (14.04) with same results.  Unmet dependences on both.  Seems that Utopic (14.10) packages need to be installed.

Not wanting to go that route, I moved on to a Mint (14.04) install and that did load 2.2.4.  I was able to pull up a terminal just like in 1.8.4, so my guess is that your missing some depends.

---

### Post by landstander on 2014-09-30
Wow ibjsb4 thank you for all the hard work your putting into this. I really wasn't expecting this level of service from the community.

_**[UPDATE:]**_
I finally got it figured out how to safely downgrade from Nemo 2.2.4 to 1.8.4, and it turns out that the same issue is present on my system even when running Nemo 1.8.4 which tells me it's not the version of Nemo that is the issue here. Also note here that I've discovered that this is not necessarily specific to Nemo at all. For example there is an "open in terminal" option if I right click on the desktop, this option also does not work same as in Nemo.
**Note:** Since the downgrade didn't solve the issue I re-upgraded Nemo back to 2.2.4 since it would be nice to get this working with the latest version.

**_Dependencies: _**
In order to build the dependencies for Nemo the following command is issued and the results shown below:
sudo apt-get build-dep nemo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

The above output shows that there was nothing to upgrade or install which given the command to build the dependencies for Nemo also shows that all of Nemo's dependencies should be met in this case.

_**Things we know so far:** _
1.) This is not necessarily an issue with features being removed via upgrade from a previous version since downgrading on my setup resulted in the same problems as before the downgrade.
2.) This is not a dependency issue since all signs point to Nemo having all of its dependencies met.
3.) This is not an issue that is specific to Nemo since the option to "open in terminal" from the right click menu on the desktop also appears to do nothing at all.

**_Questions Remaining:_**
1.) Is this a configuration issue?
2.) Is this something that is not a configuration issue but is not a bug?
3.) Is this a bug, and if so then where is the bug since this issue is no longer specific to Nemo?

**_Notes on question 1 above:_**
There are at least 4 different methods for configuration (this is something which is fundamentally flawed in Linux in my opinion, as there should only be one way to configure something as this keeps one configuration system from confusing or screwing up the settings from another configuration system. Case in point:):
1.) gconf-editor
2.) dconf-editor
3.) The command line command "gsettings"
4.) the command line command "update-alternatives"

The ideal would be if the above 4 methods of configuring something on a system all worked together flawlessly, but in my experience this isn't happening and results seem to suggest multiple databases for the configuration of things. This begs the question "which configuration database is being read by Nemo, and which one by the terminal emulator, and which one by the OS?". This seems like it might be a strange mess for anyone designing this system or users of this system to try and figure out and keep straight, and hence my confusion. (_see the section titled: Notes about how I'm still confused by all of this below_). 

**Initial statement of my confusion:** 
If I use the command gsettings I can get results that are not listed or reflected in the gconf-editor or the dconf-editor. To me this makes it seem like the command line tools are interfacing with a different database then the gconf or dconf editors might be using. Please keep reading below for more detail about why and how this is confusing.

**_[Reference:]_ Relevant listings given for a terminal by the gsettings command**:
gsettings list-recursively |grep term
org.gnome.desktop.default-applications.terminal exec-arg '-e'
org.gnome.desktop.default-applications.terminal exec '/usr/bin/lxterminal --geometry=134x80'
org.gnome.desktop.default-applications.office.calendar needs-term false
org.gnome.desktop.default-applications.office.tasks needs-term false
org.gnome.gedit.plugins.terminal foreground-color '#FFFFDD'
org.gnome.gedit.plugins.terminal palette ['#2E2E34343636', '#CCCC00000000', '#4E4E9A9A0606', '#C4C4A0A00000', '#34346565A4A4', '#757550507B7B', '#060698209A9A', '#D3D3D7D7CFCF', '#555557575353', '#EFEF29292929', '#8A8AE2E23434', '#FCFCE9E94F4F', '#72729F9FCFCF', '#ADAD7F7FA8A8', '#3434E2E2E2E2', '#EEEEEEEEECEC']
org.gnome.gedit.plugins.terminal cursor-shape 'block'
org.gnome.gedit.plugins.terminal scroll-on-output false
org.gnome.gedit.plugins.terminal use-theme-colors true
org.gnome.gedit.plugins.terminal use-system-font true
org.gnome.gedit.plugins.terminal font 'Monospace 10'
org.gnome.gedit.plugins.terminal allow-bold true
org.gnome.gedit.plugins.terminal scrollback-unlimited false
org.gnome.gedit.plugins.terminal scroll-on-keystroke true
org.gnome.gedit.plugins.terminal cursor-blink-mode 'system'
org.gnome.gedit.plugins.terminal background-color '#000000'
org.gnome.gedit.plugins.terminal audible-bell true
org.gnome.gedit.plugins.terminal scrollback-lines 20000
org.gnome.gedit.plugins.terminal word-chars '-A-Za-z0-9,./?%&#:_'
org.gnome.settings-daemon.plugins.media-keys terminal '<Control><Alt>t'
org.gnome.settings-daemon.plugins.media-keys terminal '<Control><Alt>t'
org.gnome.desktop.default-applications.office.calendar needs-term false
org.gnome.shell command-history *** This stuff omitted due to irrelevance ***
org.gnome.desktop.default-applications.office.tasks needs-term false
org.nemo.extensions.nemo-terminal default-terminal-height byte 0x05
org.nemo.extensions.nemo-terminal default-follow-mode 'Terminal follows Nemo'
org.nemo.extensions.nemo-terminal terminal-hotkey 'F4'
org.nemo.extensions.nemo-terminal terminal-restore-line '\\x19'
org.nemo.extensions.nemo-terminal terminal-change-directory-command ' cd %s'
org.nemo.extensions.nemo-terminal terminal-shell '/bin/bash'
org.nemo.extensions.nemo-terminal terminal-position 'top'
org.nemo.extensions.nemo-terminal default-visible false
org.nemo.extensions.nemo-terminal terminal-erase-line '\\x05\\x15'
org.gnome.desktop.default-applications.office.calendar needs-term false
org.gnome.desktop.default-applications.office.tasks needs-term false
org.gnome.desktop.default-applications.terminal exec-arg '-e'
org.gnome.desktop.default-applications.terminal exec '/usr/bin/lxterminal --geometry=134x80'
org.gnome.gnumeric.stf.export terminator '\n'
org.gnome.gnumeric.stf.export terminator '\n'

**Note about strange output from above:**
The above command has listed "org.gnome.desktop.default-applications.terminal" twice which makes me wonder if the database has two entries for the same thing, and why this would be a problem if those two listings were exactly the same.

**gsettings output compaired with gconf:**
Above we see "org.gnome.desktop.default-applications..." where in the gconf-editor there exists a directory tree for "/desktop/" which really isn't even close to "org.gnome.desktop..." but what the heck I looked there any way and there isn't listed any such "default-applications" directory listed there. In fact if I start at the root directory in the gconf-editor and do a search for "default-applications" where "search also in key names" and "search also in key values" is selected, this returns the results "Pattern not found". So on the one hand, gsettings shows that its storing results for a "default-applications" section that is not present anywhere in the gconf-editor. However the reference for lxterminal is listed in gconf but under a completely different directory hierarchy then gsettings is producing. (_see the section titled: Notes about how I'm still confused by all of this below_). 

**gsettings output compaired with dconf:**
When comparing whats listed by gsettings to what is given in the dconf-editor this appears to give results that gets closer but still no matches. As before gsettings gives a section called "org.gnome.desktop.default-applications..." where in the dconf-editor we can only get as close as a directory structure of "/org/gnome/", doing a search for "default-applications" from the root directory yields no results. These results and the results outlines in the previous paragraph are what make me thing that gsettings is using a different database then the gconf or dconf editors use. Here the directory reference for lxterminal in dconf is different from the directory hierarchy of either gsettings or gconf. (_see the section titled: Notes about how I'm still confused by all of this below_).

For completeness:
**_[Reference:]_ Relevant terminal listings for Nemo given by the gsettings command**:
gsettings list-recursively |grep nemo |grep term
org.gnome.shell command-history ***This stuff has been omitted due to irrelevance***
org.nemo.extensions.nemo-terminal default-terminal-height byte 0x05
org.nemo.extensions.nemo-terminal default-follow-mode 'Terminal follows Nemo'
org.nemo.extensions.nemo-terminal terminal-hotkey 'F4'
org.nemo.extensions.nemo-terminal terminal-restore-line '\\x19'
org.nemo.extensions.nemo-terminal terminal-change-directory-command ' cd %s'
org.nemo.extensions.nemo-terminal terminal-shell '/bin/bash'
org.nemo.extensions.nemo-terminal terminal-position 'top'
org.nemo.extensions.nemo-terminal default-visible false
org.nemo.extensions.nemo-terminal terminal-erase-line '\\x05\\x15'
As can be seen the only thing gsettings can configure in Nemo is the embeded terminal which as I've stated earlier isn't useful for my purposes and hence the need to use the right click "open in terminal" function.

**_Notes about how I'm still confused by all of this:_**
I'm coming from a gnome environment and working now in a Lubuntu environment so I have no idea which database Lubuntu is using for configuring an "open in terminal" from a right click menu function. Is it gconf or dconf or maybe its whatever database gsettings or update-alternatives is using? I have no idea and I'm not sure how to figure that out. On top of this, and given that I've discovered at least 4 possibly different ways of configuring things so far, it might be likely that there is yet another way of configuring how a terminal is open from a right click menu that I'm still unaware of.

**Question:**
1.) Where do we go from here in order to begin clarifying some of the above confusion?
2.) Should this question be moved to a new thread so that it is no longer highlighted by the subject line as a Nemo specific issue, but a more general "open in terminal" right click menu issue? If so then how would this be done and does this thread need a moderators attention to get it moved or the subject line fixed in some way?

---

### Post by ibjsb4 on 2014-09-30
> 2.) Should this question be moved to a new thread so that it is no longer highlighted by the subject line as a Nemo specific issue, but a more general "open in terminal" right click menu issue? If so then how would this be done and does this thread need a moderators attention to get it moved or the subject line fixed in some way?
I think your good here.  Finding help for nemo on lubuntu is going to be tough, I'm thinking not many are doing this.
> 1.) Where do we go from here in order to begin clarifying some of the above confusion?
I'm thinking you should go to nemo in Launchpad and use the 'Ask a question' option.  Maybe give them a link to this thread.

---

### Post by landstander on 2014-10-02
Ah ok, you have misunderstood.

About Question 2:
I proposed this question because it should be apparent that Nemo can no longer be considered the cause of this issue. Therefore the question about weather or not I should repost this question so that people don't get confused about it being related to Nemo is necessary.

About question 1:
I can not mark this thread as Solved since it would be impossible to solve this issue by doing anything with Nemo's settings, and since the tittle is related to Nemo there doesn't appear to be any options for how to mark this thread before I close it and reopen it as a different question. So question 1 was really being posed just to see if any one had any other idea's about how to solve this problem. However since the tittle isn't attracting any one who would be useful in solving the problem and instead only attracts people who know about Nemo, this question should probably be moved to a new thread with a title that is not specific to Nemo but instead is more general to the actual problem.

Note:
This thread has been moved to:
[http://ubuntuforums.org/showthread.php?t=2246652]("http://ubuntuforums.org/showthread.php?t=2246652")

---

