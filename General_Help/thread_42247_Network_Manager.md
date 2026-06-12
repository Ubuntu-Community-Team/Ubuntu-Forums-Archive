---
title: "Network Manager"
date: 2005-06-16
forum: General Help
---

### Post by tread on 2005-06-16
I'm trying to install this:
[http://people.redhat.com/dcbw/NetworkManager/index.html](http://people.redhat.com/dcbw/NetworkManager/index.html) 

I compiled, installed it .. and I run sudo NetworkManager .. nothing happens?!
I don't have any option to add it to the taskbar either .. 

How do I use it?!

---

### Post by karmah on 2005-06-16
Try finding the executable in the folder you installed it.
(Words from a noob though, dont trust me :D)

---

### Post by tread on 2005-06-16
Oh no, I know the executable, I'm trying to find how to use it.

---

### Post by tread on 2005-06-17
Well, NetworkManager is working .. looks pretty awesome. I plugin an Ethernet cable, it activates and gets an ip for it. I disconnect that, it starts the wireless. But that is where the problem starts. It waits for user input to connect to the network, at least the first time. For that purpose, it is supposed to show up in the notification area but it doesnt :( 

Anyone have any suggestions?

---

### Post by rwabel on 2005-06-19
it's similar to the one in ubuntu breezy. is the ubuntu one based on the redhat one?

---

### Post by blinksilver on 2005-06-19
if you went from the latest CVS then the applet is  in /usr/libexec/ i think int is called nm wireless or nm applet

---

### Post by tread on 2005-06-19
Its the same I think. For some reason I have trouble with the ubuntu one ... once I isolate the problem I shall file a bug.
Currently this is what I get on running nm-applet:

** (nm-applet:8028): WARNING **: <WARNING>        (): nmwa_dbus_init() could not acquire its service.  dbus_bus_acquire_service() says: 'Connection ":1.14" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'

---

### Post by blinksilver on 2005-06-19
try sudoing it i guess.... i don't know what to tell you, but i would like to see this fixed, because, i two, want nm working,

---

### Post by tread on 2005-06-19
sudoing it helped, but I remember not needing to do that before :???: 

I'm a little confused at the moment frankly, I compiled and installed from cvs, then saw that a breezy had it in its repos. So I uninstalled the first version, and installed the one from the repos, but there was no startup script there. Also, it seemed to crash a lot .. and took my whole machine down.

So I uninstalled it and went back to the cvs build .. its seems to be ok at the moment. I need to figure out test cases and try them, then I can file bug reports.

One problem I have is that it reports half the signal strength actually there .. if the default gnome-applet reports 80%, nm-applet reports 35-40%

---

### Post by blinksilver on 2005-06-19
they may check different strengths, that is what is happening it think, signal strength Vs signal quality, or it could be that hal uses a different mesure of signal strength, then the linux wireless extension, you really should not need to sudo, there is something wrong in one of the startup scripts, so that is what is breaking it, you have a problem with the securty setting, they are setup that only people a group can do start NM and sadly you are no in that group, so you need to hunt and fix some config files,  i will help when i get hoary running, was trying FC4, have decide that hoary is still the way to go....

---

### Post by blinksilver on 2005-06-19
oh and hope i helped otherwise

---

### Post by tread on 2005-06-19
Yes, you did .. thanks! I'm still a little confused at how startup scripts work in ubuntu ... ubm seems to make no sense to me. I better go and read some more, thats the only reason I'm not filing any bug reports yet!

---

### Post by Confuse on 2005-06-19
I'm trying to compile this using the cvs version but I get the following configure error "configure: error: iwlib. not found. Install wireless-tools." wireless-tools is already installed and locate iwlib doesn't bring anything up. Any suggestions?

---

### Post by tread on 2005-06-19
libiw27 and libiw-dev are the required packages I think.

---

### Post by Confuse on 2005-06-20
[QUOTE=tread]libiw27 and libiw-dev are the required packages I think.[/QUOTE]

Thanks that worked so far. Now to fulfill the other stuff and pray the thing compiles!

---

### Post by Confuse on 2005-06-20
Another problem....where do I get dhcdbd from? I can't find it in ubuntu repos. How were you guys able to compile from cvs with or without this? All I see are rpms.

---

### Post by blinksilver on 2005-06-20
hey tread, make it your lucky day, i have an answer, just booted, ubuntu

go to /etc/dbus-1/system.d/

inside there you will find a file called hal.conf
it looks like this

<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>

  <!-- This configuration file specifies the required security policies
       for the HAL to work. -->

  <!-- Only root or user hal can own the HAL service -->
  <policy user="hal">
    <allow own="org.freedesktop.Hal"/>
  </policy>
  <policy user="root">
    <allow own="org.freedesktop.Hal"/>
  </policy>

  <!-- Allow anyone to invoke methods on the Manager and Device interfaces -->
  <policy context="default">
    <allow send_interface="org.freedesktop.Hal.Manager"/>
    <allow send_interface="org.freedesktop.Hal.Device"/>

    <allow receive_interface="org.freedesktop.Hal.Manager"
           receive_sender="org.freedesktop.Hal"/>
    <allow receive_interface="org.freedesktop.Hal.Device"
           receive_sender="org.freedesktop.Hal"/>
  </policy>

  <limit name="max_match_rules_per_connection">512</limit>

</busconfig>

see the section about:

  <!-- Only root or user hal can own the HAL service -->
  <policy user="hal">
    <allow own="org.freedesktop.Hal"/>
  </policy>
  <policy user="root">
    <allow own="org.freedesktop.Hal"/>
  </policy>

change it to read


  <!-- Only root or user hal can own the HAL service -->
  <policy user="hal">
    <allow own="org.freedesktop.Hal"/>
  </policy>
  <policy user="root">
    <allow own="org.freedesktop.Hal"/>
  </policy>
 <policy user="YOUR_USERNAME_HERE">
    <allow own="org.freedesktop.Hal"/>
  </policy>

nowyou can have the right to start a thread, and hence can run nm-applet without sudoing, 


oh and how did you get the startup script to bootup with ubuntu

---

### Post by blinksilver on 2005-06-20
i am getting hell about the m4 forbiden macro, any idea, and yes they are installed

---

### Post by Confuse on 2005-06-20
[QUOTE=blinksilver]i am getting hell about the m4 forbiden macro, any idea, and yes they are installed[/QUOTE]

Can't really say I know what to do, but I just installed automake 1.9 and ran the script and it went through up to the part where I'm stuck at so perhaps you could ignore the error if its not debilitating to the install process? Still stumped on that dhcdb thing.... ;[

---

### Post by tread on 2005-06-20
I don't remember the dhcbd stuff .. did you try searching in synaptic using the description and name search? And whats the problem with the forbidden macro?

Also, editing hal.conf hasn't helped .. still need to sudo. I haven't got NetworkManager to start on bootup yet either .. I mean it says it has started when booting, but after that I do ps -e | grep Net and there isn;t anything. I can start the service later, and then ps show it.

I did stop the configuring network interfaces at bootup, the one that used to take forever it I had moved to a place with a different wireless network. You have to comment out some auto configure options in /etc/network/interfaces.

---

### Post by tread on 2005-06-20
It appears dhcdbd is installable in the breezy repos and not it hoary, and I'm on breezy. Just realized that.

---

### Post by blinksilver on 2005-06-20
it seems as if will just not compile in hoary, got the dhcdbd from breezy and the vpn stuff is casing a error, i put it out there maybe someone can fix it 

nm-dbus-vpn.c: In function `nm_dbus_vpn_get_vpn_data':
nm-dbus-vpn.c:199: warning: implicit declaration of function `dbus_message_iter_recurse'
nm-dbus-vpn.c:211: warning: implicit declaration of function `dbus_message_iter_get_basic'
make[3]: *** [libvpn_manager_la-nm-dbus-vpn.lo] Error 1
make[3]: Leaving directory `/home/soganess/NetworkManager/src/vpn-manager'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/soganess/NetworkManager/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/soganess/NetworkManager'
make: *** [all] Error 2
soganess@M6805:~/NetworkManager$

---

