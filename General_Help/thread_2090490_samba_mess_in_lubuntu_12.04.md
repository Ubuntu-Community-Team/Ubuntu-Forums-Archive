---
title: "samba mess in lubuntu 12.04"
date: 2012-12-02
forum: General Help
---

### Post by DrScum on 2012-12-02
Running lubuntu 12.04 on a Dell Inspiron laptop I am trying to activate file sharing with no avail.

Samba seems to be installed (available in the system tools menu) but crashes when I call it. 

When calling samba from the terminal I get the message: The program 'samba' is currently not installed.  You can install it by typing:
sudo apt-get install samba4"

When I do that the install finishes with an error message.

Any help out there?

---

### Post by DrScum on 2012-12-03
bump

---

### Post by redmk2 on 2012-12-03
> **DrScum said:**
> Running lubuntu 12.04 on a Dell Inspiron laptop I am trying to activate file sharing with no avail.

Samba seems to be installed (available in the system tools menu) but crashes when I call it. 

When calling samba from the terminal I get the message: The program 'samba' is currently not installed.  You can install it by typing:
sudo apt-get install samba4"

When I do that the install finishes with an error message.

Any help out there?
What do you mean by "crashes when I call it"?  Call what?  Samba should start automatically upon boot.  If you want to stop, start or restart it you can.  The command for this is ```
sudo service smbd [start|stop|restart]
```

When you call "samba" you are not referring to the current stable release of Samba (3.6).  In fact you are calling the unstable beta version of Samba4.

You should un-install Samba4```
sudo apt-get purge samba4
```...and insure that you have the package samba installed.  The following is what I'm talking about

```

package  application  calling binary
=======  ===========  ===============
[COLOR="Blue"]samba[/COLOR]      Samba 3.6   smbd
[COLOR="Red"]samba4[/COLOR]     Samba4      samba
```

---

### Post by DrScum on 2012-12-03
Well, I do have Samba (not Samba 4) installed on three ubuntu 12.04 machines including one Laptop and I can "call" it from the System Tools > Administration Menu.

On those machines I have no problems on those machines, but they are under ubuntu 12.04 and 10.04 respectively.

On this machine I actually have uninstalled and reinstalled samba as well as samba 4 from the repository several times but no luck. No luck means that I can't create any samba shares meaning the "sharing options" are not available in the file server right click menu, as they are on the other machines.

Crashing means that when I call it nothing happens but a system notification that an internal error occured and that I can send a message to fix the problem.

So I am going to follow your terminal commands and see what happens.

Thanks for your help

---

### Post by DrScum on 2012-12-03
I purged samba4 like you suggested and installed samba using the synaptic package manager. Now I don't know how to create a share. Do I have to use the command-line or is there a gui like on the 12.04 machines?

---

