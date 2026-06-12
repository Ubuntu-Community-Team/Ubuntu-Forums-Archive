---
title: "Installing Java in Ubuntu Gutsy..."
date: 2007-12-23
forum: General Help
---

### Post by Dojan5 on 2007-12-23
I downloaded a .bin package from Java website.
How do i now install it?
I couldn't import the file with Synaptic. I did find a website with a tutorial on HOW to use synaptic. Though, i cant understand how to use Synaptic to install Java.
Please help.

Umm, i can't find the terminal either, so if you give me Terminal Commands, please tell where to find the terminal too.
Thanks :)

---

### Post by Sef on 2007-12-23
Easy way to install Java:

Applications > Add/Remove > change the top right box to "All Available Applications" > search (type in "Sun Java 6" without the quotes) > click on the top option. > Apply > Apply > Close

---

### Post by khughitt on 2007-12-23
You can also install it through the terminal with:

**sudo aptitude install sun-java6-jre sun-java6-plugin**

The .bin files provided on Sun's website could work too, but they are more
generic binaries intended to work on a range of linux distributions. It's better in general to use a build customized specifically for your distribution when possible (e.g. .deb's for debian or Ubuntu).

---

### Post by Dojan5 on 2007-12-23
I get an error then.
It says "The list of applications is not avalible!
Press reload to Load it, to reload you need a working internet connection."
When i press reload it quickly downloads 6 files or something, then it kinda goes back to where i put this mark to install it.
Then it is unmarked, i have to mark it again and the dialog with "The list of applicatoins blah blah blah" pops up again.
And i do know i have a working internet connection, im writing this on the computer...

---

### Post by khughitt on 2007-12-23
Try opening a console (alt+f2 -> "gnome-terminal"), and typing "sudo aptitude update" followed by what I mentioned above. If you still get error messages, copy and paste them to the forums.

---

### Post by PeterJS on 2007-12-23
> **Dojan5 said:**
> I get an error then.
It says "The list of applications is not avalible!
Press reload to Load it, to reload you need a working internet connection."
When i press reload it quickly downloads 6 files or something, then it kinda goes back to where i put this mark to install it.
Then it is unmarked, i have to mark it again and the dialog with "The list of applicatoins blah blah blah" pops up again.
And i do know i have a working internet connection, im writing this on the computer...

This is getting to be my favorite gutsy "feature", when installing the installer makes some rather stupid assumptions about the state of your internet connection and it's abilty to download software, specifically it assumes that if you don't have an active connection during the install you never will so you can safely ignore all the online repositories.

To fix this, pop open synaptic and go to Settings > Repositories and make sure that the four checkboxes for the package sections are selected. After that is done try giving it another go.

---

### Post by Dojan5 on 2007-12-23
> **pwnedd said:**
> You can also install it through the terminal with:

**sudo aptitude install sun-java6-jre sun-java6-plugin**

The .bin files provided on Sun's website could work too, but they are more
generic binaries intended to work on a range of linux distributions. It's better in general to use a build customized specifically for your distribution when possible (e.g. .deb's for debian or Ubuntu).

I tried that..
This is what came up:

---

### Post by Dojan5 on 2007-12-23
> **PeterJS said:**
> This is getting to be my favorite gutsy "feature", when installing the installer makes some rather stupid assumptions about the state of your internet connection and it's abilty to download software, specifically it assumes that if you don't have an active connection during the install you never will so you can safely ignore all the online repositories.

To fix this, pop open synaptic and go to Settings > Repositories and make sure that the four checkboxes for the package sections are selected. After that is done try giving it another go.

Oh my goddess gracious!
It worked!!!
THANKSSS!!!! :) :) :) :) :) :)

===Edit===
I know someone who is going to play RuneScape this evening ^_^
Thanks again!
Wonder if flash will be the same way, and Shockwave...
I'll test when Java is done...

---

### Post by Mulenmar on 2008-03-22
Then mark your topic [SOLVED]...I saw a howto on that somewhere...

---

