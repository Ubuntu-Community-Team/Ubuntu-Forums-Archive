---
title: "How do I get Flashplayer on my daughter's log-in [Resolved]"
date: 2007-05-09
forum: General Help
---

### Post by alanmzifa on 2007-05-09
Hi, I'm trying to make it possible for my 3 yr old to to play some simple games and puzzles on the BBC's CBeebies site.

Most of the games require **Flashplayer**. I can see the games from my log-in but not the log-in I set up for her which presumably means Flashplayer isn't associating itself with **Firefox** on her log-in.

How do I rectify this?


I use Ubuntu 6.06.


thanks

---

### Post by titus1950 on 2007-05-09
Here....
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

---

### Post by alanmzifa on 2007-05-09
> **titus1950 said:**
> Here....
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

Thanks for your reply. I did that but got ...


[I]root@monty-L400laptop:/home/monty# sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree[/I]


Is there anything else I should have done?

---

### Post by DoktorSeven on 2007-05-09
Did you do the part in the link above the instructions that told you to enable extra repositories?

---

### Post by aysiu on 2007-05-09
You probably installed Flash locally instead of globally.

You can either install Flash locally again for your daughter (just visit a site that requires Flash and then follow the "install missing plugin" dialogue) or install Flash globally.

This should help:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by alanmzifa on 2007-05-09
I got it working.

Thanks to all for the help and guidance. I went back and added the PLK repositories and then it showed in Synaptic. Downloaded it and installed easily.

Sound didn't work on some sites so I used the tip from the link and all seems well now.

---

