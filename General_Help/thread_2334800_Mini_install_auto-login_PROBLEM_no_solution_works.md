---
title: "Mini install auto-login PROBLEM no solution works"
date: 2016-08-22
forum: General Help
---

### Post by raging hormones on 2016-08-22
I have ubuntu 16.04 mini install on my htpc with openbox and I want to autologin, startx and start kodi.  I got the startx thing done but cannot figure out autologin.  I have tried editing grub and following [ these ]("http://askubuntu.com/questions/175248/how-to-autologin-without-entering-username-and-passwordin-text-mode") instructions.  I have put 'exec /bin/login -f username' everywhere, in /etc/rc.local added it to a script in /etc/rc3.d I have put it in /etc/tty1.conf, I have tried various attempts using /sbin/getty I even followed the commands here [here](http://littlesvr.ca/linux-stuff/articles/autologinconsole/autologinconsole.php) which requires compiling a little login program, putting it in sbin and adding an init script.  Every time I end up at the login prompt.  I don't want to use lightdm because I want it to be as lightweight as possible (as well as the fact I shouldn't have to).  I tried using /bin/login -f username >> /home/username/login.log and the file is always empty.  Nothing in auth.log or boot.log gives useful information.  I normally don't post questions because they all have usually already been answered but I have tried every method I can find AND THEY ALL FAIL and I can't figure out why.

UPDATE:
I have also tried adding to crontab 
@reboot /bin/login -f username   and
@reboot /bin/autologin

where autologin is a c program 
int main() 
{
  execlp( "login", "login", "-f", "username", 0);
}


and I get nada.  Although /home/username/.config/openbox/autostart is pretty handy for automatically starting things in a certain order.

Edit: What the hell is up with the BB code here?
Double edit: appears fine now, was using forward slash not backslash.  Doh.

---

