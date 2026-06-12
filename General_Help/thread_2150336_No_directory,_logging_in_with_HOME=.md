---
title: "No directory, logging in with HOME=/"
date: 2013-05-31
forum: General Help
---

### Post by cerseibaggins on 2013-05-31
I have been fiddling with my computer for the last two days, browsing through forums, and nothing seems to be working to fix the problem I'm having.

I use Ubuntu 13.04.  I use a tunnel to connect to my network to get around the Great Firewall of China.  I was making adjustments to my tunnel by using the following command lines:

$!/bin/bash
mkdir -p $HOME/ .ssh/
cp $HOME/Desktop/tunnel/id_key $HOME/ .ssh/
chmod 600 $HOME/ .ssh/id_key
rm $HOME/ .ssh/known_host

My computer wouldn't let me complete the commands, froze up, and I reboot.  Since then, I've been unable to log into my root account, but I can log in as a guest.  The password is definitely correct.  

I tried running the rm ~/ .Xauthority command from the ctrl + alt +f1 screen to get access but it hasn't worked.  

in fact, when i'm in the ctrl alt f1 screen, it says 'no driectory, logging in with HOME=/.  I find that to be curious.  

i've tried to move files by loading a live cd with ubuntu on it, but i can't even view any of the files without root permission.  

at this point, i'm starting to give up hope and i'm thinking that my files might be unrecoverable. i don't understand what i did wrong.

help!!! thanks!

---

### Post by vanadium on 2013-06-01
This command says:
```

 chmod 600 $HOME/ .ssh/id_key

```

That command has reset the permissions of your $HOME directory to 600. Your home directory therefore is not anymore accessible (because not executable). Try resetting the permissions to the default 755 (or alt least 700) and see if it works again.

If it still fails, then just reinstall without reformatting your partitions. This goes quite fast, and usually repairs what is broken without loosing too much of your settings. If that still fails, then reinstall again the same way, but first move your old home out of the way (rename it). That way, a new account will be created, and there is guarantee that you will be able to log in. You can then move your data back from the old homedirectory to the new one.

Your commands as you showed them may have created more havoc. In many instances, there is a space between $HOME/ and the other elements, which causes these to be considered as multiple arguments rather than one pathname. In the example I gave, the permissions were not only applied to .ssh/id_key in your home directory but also to $HOME/ itself. Be careful with the commandline!

---

### Post by Impavidus on 2013-06-01
In fact, with```
rm $HOME/ .ssh/known_host
```you instructed your shell to delete your home directory. It probably failed, as it wasn't empty. Again with the rm ~/ .Xauthority.

---

