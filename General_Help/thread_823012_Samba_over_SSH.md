---
title: "Samba over SSH"
date: 2008-06-08
forum: General Help
---

### Post by sparrowkc on 2008-06-08
STOP!!!
I know there are a bazillion tutorials out there for doing this.  All of them explain how to ssh into a remote Linux machine from a local Windows machine.  I have a different situation.

I am sitting here on my Linux laptop away from home.  I have a windows computer at home with shared folders.  My home router runs DD-WRT, and has a ssh server running on it.  I assume I want to forward port 139 between the router and my laptop over ssh.  I have never really understood port forwards (-D vs. -L), but I gather I want 
```
ssh  -C -L 139:localhost:139 -p sshlistenport root@routerpublicip
``` or ```
ssh  -C -L 139:routerpublicip:139 -p sshlistenport root@routerpublicip
```

Problem is both of those throw this error
```
bind: Address already in use
channel_setup_fwd_listener: cannot listen to port: 139
Could not request local forwarding.

```

Which goes away when I untick samba filesharing in services, but I don't think a port forward would do me any good if I don't have samba running...

Help?

---

### Post by sparrowkc on 2008-06-08
Please?

---

### Post by Rocket2DMn on 2008-06-08
If you have your router configured correctly, you should just have to ssh into your public IP (owned by the router) and it will forward you to the desktop computer.  So say you have port 137 visible externally.  Regardless of what port ssh is running on internally, you would ssh to public_ip:137
That means if you have the server running on port 137, that's fine, but even if you have port triggering enabled (say the server runs port 22 but you had the router show port 137 to the outside world), you still connect to port 137 and the router takes care of the rest.
```
ssh home_public_ip:port
```

---

### Post by Junosix on 2008-07-01
Did you manage to resolve this?  I'm having exactly the same problem - i.e. if Samba's already running on the machine I want to share the files too then it can't bind port 139.  Of course turning Samba off allows this but the obvious results of then not being able to use Samba!

---

### Post by dburnett77 on 2008-07-01
> **sparrowkc said:**
> STOP!!!
I know there are a bazillion tutorials out there for doing this.  All of them explain how to ssh into a remote Linux machine from a local Windows machine.  I have a different situation.

I am sitting here on my Linux laptop away from home.  I have a windows computer at home with shared folders.  My home router runs DD-WRT, and has a ssh server running on it.  I assume I want to forward port 139 between the router and my laptop over ssh.  I have never really understood port forwards (-D vs. -L), but I gather I want 
```
ssh  -C -L 139:localhost:139 -p sshlistenport root@routerpublicip
``` or ```
ssh  -C -L 139:routerpublicip:139 -p sshlistenport root@routerpublicip
```

Problem is both of those throw this error
```
bind: Address already in use
channel_setup_fwd_listener: cannot listen to port: 139
Could not request local forwarding.

```

Which goes away when I untick samba filesharing in services, but I don't think a port forward would do me any good if I don't have samba running...

Help?

Remain forever pesky.  Seriousness can lead to:

Death, lawsuits, fist-face, all sorts of maladies.

---

### Post by Junosix on 2008-07-02
Great, thanks.

---

### Post by MagnusPg on 2010-06-24
> **sparrowkc said:**
> I am sitting here on my Linux laptop away from home.  I have a windows computer at home with shared folders.  My home router runs DD-WRT, and has a ssh server running on it.  I assume I want to forward port 139 between the router and my laptop over ssh.


Hi everyone!

I know this is a bit of a late reply but I believe this is still an issue for some and as such deserves a response.
Please note that these instructions are valid only for Windows machines that use the new sharing port 445 such as Windows 2k/XP/Vista/7 etc.
It should also work for most samba enabled NAS devices out there. It may work with older Windows versions that use port 139 for file sharing but as I have never tried it myself 
I make no guarantees.


To try to explain what is being attempted:

Setup is as follows:
Linux laptop client
    |
    | Internet
    |
*nix based router/computer
    |
    | LAN
    |
Windows machine with shared folders (or similar)

Note first, the linux client does not have to have samba services enabled as it will only be a client in this case.
Samba is kind of an annoying sharing method as it pretty much must use port 445 as most samba enabled applications doesn't allow a port to be specified (apart from *nix gui-less clients)

What you will want to do is first stop samba from listening on your localhost, either by disabling it

```
sudo /etc/init.d/samba stop
```
or specify which interface you want your samba service to use (refer to "man smb.conf" search for "bind interfaces only", please note the specified issues resulting from this method)

After you have done this what you will want the ssh process to do is to forward your localhost port 445 to your windows machine port 445.
The limitation of forwarding a lower numbered port with ssh is that you have to be root to do so, thus:

```
sudo ssh -L 127.0.0.1:445:WindowsIP:445 -Nf RouterUser@RouterInternetAddress
```
After entering first your local password (for sudo) and router password (for ssh) your should be able to do:

```
smbclient --user=WindowsUser //localhost/WindowsShare
```
You can also use nautilus (gnome default file manager) by using

Go -> Location -> smb://localhost/WindowsUser/

Note:
The ssh command above allows connections only from localhost meaning your Linux machine, it will not give any other computer access to your windows shares. If that is what your want you can change 172.0.0.1 to your computers ip and add -g to allow remote hosts to connect.
Please not that this is a potential security risk depending on your location as opening this port on an open network will allow anyone access to your windows machines shares.
It will still be password protected but it's a far cry from sitting behind a dd-wrt router.

---

