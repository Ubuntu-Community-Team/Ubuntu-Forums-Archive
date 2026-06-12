---
title: "Shutdown Problem"
date: 2008-05-26
forum: General Help
---

### Post by notesetter on 2008-05-26
Hi,

I'm copying this post that I made in Laptops/Hardware to this this forum. It sat there unanswered for two plus weeks, so I'm hoping someone who views this area of the forums can shed some light. Sometimes I get this message and then it shuts down. Sometimes the message appears and it hangs for several minutes before I finally pull the battery (I think the longest I've waited is around 10 minutes.)

It's a Compaq Presario 2170US, 2.0 Ghz, 80 Gb HDD, 256 MB RAM, Ubuntu Studio 8.04

Thanks.

Hello,

Sometimes when I shut down my Compaq Presario Laptop (It doesn't hibernate or suspend) it goes through its shutdown routine, the "closing" splash screen acts as expected, and then I get this message or something like it:

NetworkManager: <WARN> nm_signal_handler(): Caught signal 15, shutting down normally.

NetworkManager: <info> Cuaght termination signal

NetworkManager: <debug> [1210108670.020308] nm_print_open_socks(): Open Sockets List:

NetworkManager: <debug> [1210108670.021162] nm_print_open_socks(): Open Sockets List Done

NetworkManager: <WARN> nm_dbus_init(): nm_dbus_init() could not get the system bus. Make sure the message bus daemon is running!

It doesn't go further than this. It usually ends with me unplugging the power cord and then popping out the battery.

Anyone want to take a crack at it?

It may be worth noting that it's a dual-boot system running Windows XP home on a primary partition.

Thanks,

Dave

---

### Post by Samhain13 on 2008-05-26
I just had the same thing a couple of hours ago when I shutdown.
I've been experiencing this when I newly installed Hardy but the situation went away for a while. But now, it's back.

I don't know how to fix it, but you can try logging out frist and shutting down from the login screen.

---

### Post by cwbar_1 on 2008-05-26
Have you tried any of the posts in this thread?  (mpince is correct! I guess I didn't pay attention to which URL I pasted. Hope I didn't cause any confusion)

---

### Post by mpince on 2008-05-26
I think he means this thread (see post #13):


[http://ubuntuforums.org/showpost.php?p=4858236&postcount=13](http://ubuntuforums.org/showpost.php?p=4858236&postcount=13)

---

### Post by notesetter on 2008-05-26
mpince and cwbar_1,

I tried the fix suggested on the post and it doesn't seem to work. As I (foolishly) didn't make a note of the default commands in those fields, do either of you happen to know what they were or where I can find them? That way I can restore them since they at least worked somewhat better than the proposed fix.

To all, might this be a RAM problem? I know I'm running a little short on memory and I'm planning to upgrade soon.

Thanks,

---

### Post by cwbar_1 on 2008-05-26
The defaults are:/sbin/shutdown -h now "Shut Down via gdm." for the halt command and /sbin/shutdown -r now "Rebooted via gdm." for the reboot. 
BTW.... My shutdown and reboot problems were corrected with the latest update. (today, which included a new kernel) I am also running WICD instead of the gnome network manager.  I'm running an HP Pavilion dv6449us with envy installed Nvidia Geforce Go 6150.  The only problem remaining for me is shutdown with battery power only.  The splash screen "Ubuntu' is double on the horizontal plane.

---

