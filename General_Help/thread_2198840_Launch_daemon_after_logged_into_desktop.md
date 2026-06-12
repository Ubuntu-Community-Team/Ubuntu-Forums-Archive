---
title: "Launch daemon after logged into desktop"
date: 2014-01-10
forum: General Help
---

### Post by cartpauj on 2014-01-10
I'm working on reviving an old Thinkpad Z60t with Lubuntu. I found a small daemon called tpb (thinkpad buttons) that shows some on-screen pop-ups when I press the quick launch buttons on the keyboard.

Basically I need to run this command with root privileges sometime after an X session is running. I tried /etc/rc.local but that is too soon apparently. Any other ideas?

Command:
/usr/bin/tpb -d --config /home/{user}/tpbconfig.tpbrc

I'd really prefer not to mess with the sudoers file if at all possible. Thanks!

---

### Post by tomearp on 2014-01-10
[This post]("http://askubuntu.com/questions/30931/how-do-i-make-a-program-auto-start-everytime-i-log-in") has some different approaches you might like to try.

To run the command as root I don't think you'll have much choice but to use sudo. The sudoers file can be configured [to allow specific commands without a password]("http://www.linuxquestions.org/questions/linux-newbie-8/setting-up-user-to-use-sudo-for-specific-commands-856928/").

---

### Post by cartpauj on 2014-01-12
Thanks for tips. Ok here's where I'm at and I'm hoping you or someone else can find where I've messed this up, because I still can't get it working.

1) My {user} is in the sudo group. So that's all good.

2) I've edited the /etc/sudoers file using visudo in the shell run as root, and added this line:
> {user}        ALL = NOPASSWD: /usr/bin/tpb -d --config=/home/{user}/touch_pad_button_config.tpbrc

3) In /home/{user}/.config/autostart/ I've added a file with the following contents:
> 
[Desktop Entry]
Type=Application
Name=TPB autostart
Comment=Start Thinkpad Buttons daemon
Exec=sudo /usr/bin/tpb -d --config=/home/{user}/touch_pad_button_config.tpbrc


4) I've also tried this line instead in the sudoers file but no luck either:
> {user}        ALL = NOPASSWD: /usr/bin/tpb

I feel like I'm getting close, but not sure what I've missed. Thanks again for any help!

---

### Post by tomearp on 2014-01-12
I would say that
```
{user} ALL = NOPASSWD: /usr/bin/tpb
```
is the correct entry in the sudoers file

If you login as the defined user, then open a terminal and manually run
```
sudo /usr/bin/tpb -d --config=/home/{user}/touch_pad_button_config.tpbrc
```
does it work successfully? If it complains or asks for a password etc. then it would suggest something in sudoers is the issue. If it runs fine then that would suggest it's an issue with the autostart.

The location of your entry in the sudoers file (relative to other entries) can result in unexpected effects.
[This is worth a read]("https://help.ubuntu.com/community/Sudoers#The_Default_Ubuntu_Sudoers_File"), especially the last sentence of the "Default Ubuntu Sudoers File" section.

---

### Post by cartpauj on 2014-01-13
Thank you very much! Got it working finally, here's what I did.

1) In /etc/sudoers near the bottom of the file:
> {user} ALL = NOPASSWD: /usr/bin/tpb

2) In /home/{user}/.config/lxsession/Lubuntu/autostart at the bottom of the file (note that I'm not using @ on this line)
> sudo /usr/bin/tpb -d --config=/home/{user}/touch_pad_button_config.tpbrc

Hope that helps someone else as well :D

---

### Post by tomearp on 2014-01-13
No problem, glad to help.

At the top of the post there is a Thread Tools menu; you can select to mark the thread as solved which may be helpful to people in the future :)

---

