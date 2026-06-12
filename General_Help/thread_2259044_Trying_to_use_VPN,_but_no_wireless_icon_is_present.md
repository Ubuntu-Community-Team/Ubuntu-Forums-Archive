---
title: "Trying to use VPN, but no wireless icon is present."
date: 2015-01-01
forum: General Help
---

### Post by matthew66 on 2015-01-01
I am using the tutorials on EarthVPN ([http://www.earthvpn.com/linux-desktop-pptp-setup-guide/](http://www.earthvpn.com/linux-desktop-pptp-setup-guide/)),  to connect Ubuntu to their servers. The  network icon is not present in the upper-right corner of my computer screen. I have gone  into network connections and set up everything else as the tutorial  said, but the connection still isn't active. I'm guessing this is  because I can't do step 7. 

I also posted this question at [http://www.reddit.com/r/linux/comments/2qyfqg/trying_to_connect_to_a_vpn_but_there_is_no/](http://www.reddit.com/r/linux/comments/2qyfqg/trying_to_connect_to_a_vpn_but_there_is_no/), and followed the advice there, but it didn't work.

---

### Post by mikewhatever on 2015-01-02
What Ubuntu release do you use? All of them shold have the Network Manager preinstalled, and the applet autostarted. The icon should be somewhere (uless it is a derivative that comes without) - top right in Ubuntu and Xubuntu, bottom right in Lubuntu and Kubuntu. You can also launch it from a terminal window with <nm-applet>.

---

### Post by matthew66 on 2015-01-02
I have Ubuntu Studio. It was there when I first downloaded the OS but disappeared a few months ago after I'm guessing I somehow deleted it. 

I've since reinstalled it to make sure. Here is the message when I run "nm-applet" in the Terminal.

matthew@matthew-HP-2000-Notebook-PC:~$ nm-applet
nm-applet-Message: using fallback from indicator to GtkStatusIcon

(nm-applet:14783): nm-applet-WARNING **: Could not find ShellVersion property on org.gnome.Shell after 5 tries

---

### Post by monkeybrain20122 on 2015-01-03
Is it similar to this issue? [http://ubuntuforums.org/showthread.php?t=2257371&p=13191296#post13191296](http://ubuntuforums.org/showthread.php?t=2257371&p=13191296#post13191296)

If so, please add an affect me too to the bug report  in my last post. As I reported in the bug report, a temporary workaround would be to either wait for a bit before initial login or logout and then login again (or you may can use the command line and bypass the nm-applet, depending on your setup, that always works)

---

