---
title: "Problem with Sudo"
date: 2005-10-20
forum: General Help
---

### Post by scpike on 2005-10-20
when I try to run the sudo command, i get: 

unable to lookup  via gethostbyname()

also when I try to log into gnome it gives me the error:

"Could not look up internet address for ."


I've been running breezy without problems for a few weeks now, but all of a sudden its stopped letting me do anything that takes superuser priveledges (network configuration for example) or editing config files

any help is appreciated thanks

edit:
when I try to run beagled, I get the followin error:

> Unhandled Exception: System.Net.Sockets.SocketException: No such host is known
in [0x00033] (at /tmp/scratch/BUILD/mono-1.1.9.2/mcs/class/System/System.Net/Dns.cs:174) System.Net.Dns:GetHostByName (string)
in [0x0002d] (at /tmp/scratch/BUILD/mono-1.1.9.2/mcs/class/System/System.Net/Dns.cs:203) System.Net.Dns:Resolve (string)
in [0x00054] (at /tmp/scratch/BUILD/mono-1.1.9.2/mcs/class/System.Runtime.Remoting/System.Runtime.Remoting.Channels.Tcp/TcpServerChannel.cs:72) System.Runtime.Remoting.Channels.Tcp.TcpServerChannel:Init (System.Runtime.Remoting.Channels.IServerChannelSinkProvider)
in [0x001b3] (at /tmp/scratch/BUILD/mono-1.1.9.2/mcs/class/System.Runtime.Remoting/System.Runtime.Remoting.Channels.Tcp/TcpServerChannel.cs:137) System.Runtime.Remoting.Channels.Tcp.TcpServerChannel:.ctor (System.Collections.IDictionary,System.Runtime.Remoting.Channels.IServerChannelSinkProvider)
in [0x00020] (at /tmp/scratch/BUILD/mono-1.1.9.2/mcs/class/System.Runtime.Remoting/System.Runtime.Remoting.Channels.Tcp/TcpChannel.cs:63) System.Runtime.Remoting.Channels.Tcp.TcpChannel:Init (System.Collections.IDictionary,System.Runtime.Remoting.Channels.IClientChannelSinkProvider,System.Runtime.Remoting.Channels.IServerChannelSinkProvider)
in [0x00034] (at /tmp/scratch/BUILD/mono-1.1.9.2/mcs/class/System.Runtime.Remoting/System.Runtime.Remoting.Channels.Tcp/TcpChannel.cs:54) System.Runtime.Remoting.Channels.Tcp.TcpChannel:.ctor (int)
in <0x00048> Beagle.WebService.WebBackEnd:init ()
in <0x00255> Beagle.WebService.WebServiceBackEnd:Start ()
in <0x001b1> Beagle.Daemon.BeagleDaemon:StartupProcess ()
in <0x00047> (wrapper delegate-invoke) System.MulticastDelegate:invoke_bool ()
in <0x0002a> IdleProxy:Handler ()
in <0x0002b> (wrapper native-to-managed) IdleProxy:Handler ()
in (unmanaged) 0xb7f4a74f
in <0x00004> (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x005a3> Beagle.Daemon.BeagleDaemon:Main (string[])


is this refering to the same host problem?



also if i type "hostname" at the command prompt it comes back blank

---

### Post by scpike on 2005-10-20
nothing?

---

### Post by drogoh on 2005-10-20
You have no hostname set.  Boot into 'recovery mode' and set a hostname in the correct file, /etc/HOSTNAME I *think*.  During your install, when the installer prompted you for a hostname, did you just backspace away the default of 'ubuntu'?

Edit:  I'm currently working in Windows, so I can't boot into Ubuntu and verify the file name, it's in /etc though...

Edit2:  It's lower case, /etc/hostname  Thanks, Kass. :D

---

### Post by scpike on 2005-10-20
when i set it up i made the hostname my name, stephen
now my hostname file is blank, can i just set it back to anything and restart?
i have to go into recovery mode to get permisssions to change it right

---

### Post by drogoh on 2005-10-20
[QUOTE=scpike]
i have to go into recovery mode to get permisssions to change it right[/QUOTE]

From what my eyes can see, yes.

---

### Post by scpike on 2005-10-21
ok i went under recovery mode and added a name to the hostname file,
but now when i try sudo it says:

sudo: unable to lookup stephen via gethostbyname()

(the hostname i set was stephen)

any ideas?

my /etc/hostname file is:
stephen

my /etc/hosts file is:
> 127.0.0.1 localhost.localdomain localhost 

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by wahur on 2005-10-21
Your /etc/hostname is now OK.
But /etc/hosts should say

127.0.0.1 localhost.localdomain localhost stephen

You can find more info on the bug and solutions if you search Ubuntu forums for 'getbyhostname()'

Wahur, been there, done that

---

