---
title: "send message to user's GUI through command line"
date: 2013-03-25
forum: General Help
---

### Post by Synoc on 2013-03-25
presently I am running Ubuntu 10.04 on multiple old PCs in my house. if it were just MY PCs I  would be fine, however, the problem comes in when I have to factor in people who are Windows all the way and can't figure out Update Manager. So to avoid the headaches I am remoting into their computers via ssh, if there is a kernel update that requires a restart I normally just restart their computer for them as well. However before i do that I run "who" to see if they are on. If they are I cannot restart their computer.

I would LIKE to be able to, from the command line, send a message to their GUI informing them they will need to restart their computer after they have concluded their business for the time being. Is this possible? so we are clear, I have my own account with sudoer permissions to administrate this account.  I would be sending the message from my account (on the CLI) to their account (preferably a popup window in their GUI).

---

### Post by matt_symes on 2013-03-25
Hi

I have read, but never tried, that samba can do this for you.

```
echo "Going for reboot now" | smbclient -M <cmputer_name>
```

Now this i do know for sure: You can get the computer names using

```
nbtscan 192.168.0.0/24
```

This will scan the class C subnet 192.168.0.0/24 and you will have to change as appropriate for your network.

It's in the package...

```
matthew-S206:/home/matthew % apt-cache search nbtscan
nbtscan - A program for scanning networks for NetBIOS name information
matthew-S206:/home/matthew % 

```

You can get extra information using

```
nmblookup -A 192.168.0.104
```

Tell us how it goes.

**EDIT:**

Did i misunderstand you ? Are they on Windows or Linux machines, as the above solution if for sending messages to Windows machines from a Linux box.

If your ssh'ing into a linux box to reboot it then something like this should work (assuming you have notify-send)

```
DISPLAY=:0.0 notify-send "REBOOTING IN 5 MINUTES" "Your PC will be rebooted in 5 Minutes. Please save all your files"
```

Kind regards

---

### Post by Synoc on 2013-03-25
trying the notify send worked fine on my computer, however when I ssh'd into the other computer and tried (had to install the program first) I got this message

> 
DISPLAY=:0.0 notify-send "Your Operating system has been updated. when you have finish with your business, please restart the computer. Thank you."
libnotify-Message: Unable to get session bus: /bin/dbus-launch terminated abnormally with the following error: No protocol specified
Autolaunch error: X11 initialization failed.




** (notify-send:5797): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed


** (notify-send:5797): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed


** (notify-send:5797): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed
libnotify-Message: Unable to get session bus: /bin/dbus-launch terminated abnormally with the following error: No protocol specified
Autolaunch error: X11 initialization failed.




** (notify-send:5797): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed


** (notify-send:5797): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed


thank you for your help thus far

---

### Post by matt_symes on 2013-03-25
Hi

Are you logging in as the same user as the user who is logged on ?

I assume this is a session dbus error but i may be wrong.

Kind regards

---

### Post by Synoc on 2013-03-25
no, my own account.

---

### Post by steeldriver on 2013-03-25
I'm not able to recreate your exact error, but I'd expect you'd either need to grab the remote user's DBUS_SESSION_BUS_ADDRESS or at least their Xauthority - the old school way would probably be to have the remote user open up their session authority using 'xhost +', however I think it's recommended to avoid that if possible

FWIW this works for me (it assumes your ssh user can read the remote user's $HOME/.Xauthority using sudo):

```

steeldriver@htpc-01:~$ xauth list    # we are logged in via ssh and don't have any valid Xauthority cookies 
steeldriver@htpc-01:~$
steeldriver@htpc-01:~$ sudo cat /home/*remote-user*/.Xauthority | xauth merge -
steeldriver@htpc-01:~$ xauth list    # now we should have a cookie for the active remote display
htpc-01/unix:0  MIT-MAGIC-COOKIE-1  c7eb54429f6b730cd89eea184c352bfc
steeldriver@htpc-01:~$
steeldriver@htpc-01:~$ DISPLAY=:0 notify-send test 'This is a test'
steeldriver@htpc-01:~$

```

It's probably not strictly necessary, but you can revoke the grabbed Xauthority after with
```

steeldriver@htpc-01:~$ xauth remove htpc-01/unix:0

```

---

### Post by matt_symes on 2013-03-25
Hi

> no, my own account.

That'll be a problem then. 

You'll certainly want a X server cookie so follow steeldriver's post to get the users X cookie.

Post back on how you get on.
> 
the old school way would probably be to have the remote user open up  their session authority using 'xhost +', however I think it's  recommended to avoid that if possible

I believe it's classed as a security risk.

Kind regards

---

### Post by Synoc on 2013-03-25
steel's tutorial fails at the 
```

sudo cat /home/remoteuser/.Xauthority \ xauth merge - 

```
there is no .Xauthority in the user's home directory

---

### Post by steeldriver on 2013-03-25
My apologies, I just checked and that command doesn't work if the ssh user doesn't have an existing .Xauthority file to merge the remote session's cookie into

You can either create an empty ~/.Xauthority (mode should be 600 i.e. -rw-------) or try this which I *think* will create the file if it doesn't already exist

```
sudo cat /home/*remote-user*/.Xauthority | xauth [COLOR=#0000ff]**-f ~/.Xauthority**[/COLOR] merge -
```

---

### Post by Synoc on 2013-03-26
```

sudo cat /home/<remote-user>/.Xauthority | xauth -f ~/.Xauthority merge -
xauth:  creating new authority file /home/me/.Xauthority
cat: /home/<remote-user>/.Xauthority: No such file or directory
xauth: (argv):1:  unable to read any entries from file "(stdin)"

```

no joy

what account should own the .Xauthority file?

---

### Post by steeldriver on 2013-03-26
<remote-user> refers to the user whose X session you are trying to pop the message up on - you are trying to grab the magic cookie that will let your notify-send talk to their X session

If <remote-user> doesn't have a .Xauthority (or it's in a non-standard location i.e. not the user's home dir) then I'm clueless - sorry

---

### Post by matt_symes on 2013-03-26
Hi

Just to reiterate steeldriver...

```
cat /home/**<remote-user>**/.Xauthority | ...
```

Change the bolded remote user to the name of the user to send the message to.

<remote-user> is just a place holder for a user name.

If they have no X session then use the command

```
wall
```

From ```
man wall
```

> Wall displays the contents of file or, by default, its standard input, on the terminals of all currently logged in users.

I suspect they have an X session though.

Kind regards

---

### Post by Synoc on 2013-03-26
I put the real user in place of <remote-user>, for privacy sake I put it back in for posting here.

---

### Post by Synoc on 2013-03-26
> **steeldriver said:**
> <remote-user> refers to the user whose X session you are trying to pop the message up on - you are trying to grab the magic cookie that will let your notify-send talk to their X session

If <remote-user> doesn't have a .Xauthority (or it's in a non-standard location i.e. not the user's home dir) then I'm clueless - sorry

also, when I do the "xauth list" it says it is creating /home/me/.Xauthority in my home directory, but an ls -A does not show one for me either.

---

### Post by steeldriver on 2013-03-26
Hmm

I guess it could be a matter of the remote user's permissions - both the machines I tested it on have the default Ubuntu umask, making the remote user's home dir drwxr-xr-x

Another way that works for me (at least when the remote session is running under lightdm) is to grab the root cookie:

```
sudo sh -c 'DISPLAY=:0 XAUTHORITY=/var/run/lightdm/root/:0 /usr/bin/notify-send test "This is a test"'
```

---

### Post by Synoc on 2013-03-26
default umask is in place.

---

### Post by markbl on 2013-03-26
> **Synoc said:**
> 
I would LIKE to be able to, from the command line, send a message to their GUI informing them they will need to restart their computer after they have concluded their business for the time being. Is this possible? so we are clear, I have my own account with sudoer permissions to administrate this account.  I would be sending the message from my account (on the CLI) to their account (preferably a popup window in their GUI).
Wouldn't it be easiest to just use MSN or Skype or Google Talk etc? Just initiate a group chat to pop up the dialog on all users PCs. I've not tried it but you can also use Empathy or Pidgin with the Bonjour protocol to discover and chat to local LAN users without a server. May be worth looking at?

---

### Post by Synoc on 2013-03-26
regrettably, IM programs are not on the agenda. it is looking like I will have to su into the user account and inform them or else schedule the PC to restart around 4 AM when I am certain it will not be use. less efficient, but it will do the job.

---

