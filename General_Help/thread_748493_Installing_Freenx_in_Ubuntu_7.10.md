---
title: "Installing Freenx in Ubuntu 7.10"
date: 2008-04-07
forum: General Help
---

### Post by Don PinPon on 2008-04-07
Hi all

First of all, i'm new in Ubuntu, so be patient :)
Well, I'm trying to install Freenx in my Ubuntu 7.10, i have followed these steps:

1) aptitude install freenx --> Everything Ok
2) Reconfigure my sshd to a new port
3) Change etc/nxserver/node.conf with the new sshd port 

and now the guide that i'm following says that i have to run:

4)  nxsetup --install --clean

But i get this error:

```

------> It is recommended that you use the NoMachine key for
        easier setup. If you answer "y", FreeNX creates a custom
        KeyPair and expects you to setup your clients manually.
        "N" is default and uses the NoMachine key for installation.

 Do you want to use your own custom KeyPair? [y/N] y
Removing special user "nx" ...done
Removing session database ...done
Removing logfile ...done
Setting up /etc/nxserver ...done
Setting up /var/lib/nxserver/db ...done
Setting up /var/log/nxserver.log ...done
Setting up special user "nx" ...Aviso: El directorio personal que especificó ya existe.
Agregando usuario del sistema `nx' (UID 112) ...
Agregando nuevo usuario `nx' (UID 112) con grupo `nx' ...
El directorio personal '/var/lib/nxserver/home' ya existe.  No se lo copia desde '/etc/skel'.
adduser: Atención: el directorio personal no pertenece al usuario que está creando.
Contraseña cambiada.
done
Setting up known_hosts and authorized_keys2 ...done
Setting up permissions ...done
Setting up cups nxipp backend ...done

----> Testing your nxserver configuration ...
Warning: Could not find nxdesktop in /usr/lib/nx. RDP sessions won't work.
Warning: Could not find nxviewer in /usr/lib/nx. VNC sessions won't work.
Warning: Invalid value "APPLICATION_LIBRARY_PRELOAD=/usr/lib/libX11-nx.so.6.2:/usr/lib/libXext-nx.so.6.4:/usr/lib/libXcomp.so.3:/usr/lib/libXcompext.so.1:/usr/lib/libXcompshad.so.3:/usr/lib/libXrender-nx.so.1". /usr/lib/libXcompext.so.1 could not be found. Users will not be able to run a single application in non-rootless mode.
Warning: Invalid value "COMMAND_FOOMATIC=/usr/lib/cups/driver/foomatic-ppdfile"
         Users will not be able to use foomatic.
Warning: Invalid value "DEFAULT_X_SESSION=/etc/X11/xdm/Xsession"
         Users might not be able to request a default X session.
Warning: Invalid value "COMMAND_START_CDE=cdwm"
         Users will not be able to request a CDE session.
Warning: Invalid value "COMMAND_SMBMOUNT=smbmount". You'll not be able to use SAMBA.
Warning: Invalid value "COMMAND_SMBUMOUNT=smbumount". You'll not be able to use SAMBA.
**Error: Could not find 1.5.0 or 2.[01].0 or 3.0.0 version string in nxagent. NX 1.5.0 or 2.[01].0 or 3.0.0 backend is needed for this version of FreeNX.**

  Errors occured during config check.
  Please correct the configuration file.

```

I'm not sure how to fix this error, i'm thiking that is some missed dependencies but i don't know. I have searched the forum for similar freenx errors, but i didn't find anything. Can you give me any tips?

Thanks in advance for your answers.
BR. Don PinPon

---

### Post by FakeOutdoorsman on 2008-04-07
Did you try these instructions from the Ubuntu Wiki: [FreeNX]("https://help.ubuntu.com/community/FreeNX")?

---

### Post by Don PinPon on 2008-04-08
Hi

I have tried that link, the difference with the guide that I'm using is this:

```
sudo nxserver --adduser <username> 
sudo nxserver --passwd <username>
sudo nxserver --restart
```

So i have done it; and also i have tried this:

```
sudo nxsetup --install --setup-nomachine-key --clean --purge
```

instead of

```
sudo nxsetup --install --clean
```

But i get the same error than, but the strange thing is that after executing nxserver --restart, i get the message that the nx server is up an running :s; therefore i have installed the nxclient and i have tried to connect to my localhost and it worked!! 

i don't understand how the server is running, and where is the freenx process? when i execute, as root, ps -A i don't see any nx process .. :s; anyway my freenx works and that was the objective; i'll try to get info about that error and if i think that is useful for the community, i'll post it here

Thanks,

---

