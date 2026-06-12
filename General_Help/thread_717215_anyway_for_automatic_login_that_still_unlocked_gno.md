---
title: "anyway for automatic login that still unlocked gnome keychain?"
date: 2008-03-06
forum: General Help
---

### Post by rob_peer on 2008-03-06
i have a dekstop with wireless.
i dont need password security login, as its in my room, but i need to unlock gnome keychain so it will connect to my WPA2 router.
is this possible?

---

### Post by LeoSolaris on 2008-03-06
well...  I am still fairly new, but I have been using Ubuntu for a couple of months now, so time to try helping. 

Let me see if I have this straight...   your wireless has no password on it, but ubuntu is not connecting to it? Do you still have the notification bar on your panel? If so there is a networking icon on it, or should be, sometimes it bugs out on me and vanishes, I just log out and back in, usually resets it. You have to use that networking icon to access the list of available wireless connections, or at least I have not found another way to do it.

The act of choosing it and shutting down with it still active should make it a default wireless connection all by itself. That is why I never have to actually click on the public wireless signal at my college library. All I do is turn my computer on and it will automatically locate the connection and connect, since there is no password. Ubuntu is supposed to look for wireless points that it has already used automatically.

It may be, since you were not exactly clear there, that you have passworded the keychain... That is changeable in the Manager as well. Just go to view up at the top, (or hit F9 it's the short cut key in Keyring Manager to view all of the keyrings)

If you have passworded your wireless as your WPA2 router comment suggests (since WPA2 is a type of encryption for passwords on routers not a type of router), all you need to do is say yes to the little pop up asking to give nm-applet permission to have access to the keyring. That means you are giving the applet permission to store the password and access it on demand via the keyring manager (password manager), otherwise you will have to enter the password every time because you told the system not to store it.

You can always check your keyrings by going to menu->System->Administration->Keyring Manager. Select the passphrase for the connection you want, then click the Applications tab and make sure that nm-applet has read, write, and delete privileges. The really important point is to make sure it has read privileges, otherwise the tool that connects you can't actually use the password.

Hopefully one of those pieces of information will be useful. I am not 100% sure what you were asking, since I have not had to enter a password to access my wireless net in a long time. It should have stored that for you and let the applet have the password automatically on login.

On a side note, even if it is your room, a wireless connection can be picked up a long way off, and really should be password protected with as strong an encryption as possible, to at least deter casual bandwidth thieves. 

Hope it helps!
Leo

---

### Post by LeoSolaris on 2008-03-06
Oh! I re-read your question...   ok Maybe I am jsut blind, but now I understand, I think. You have auto -login for your desktop when it starts up, but it still asks you for a password to access the keyring because your not an admin.  Just go to Menu->System->Administration->Login Window, then on the tabs at the top, select security. Check the box next to allow local system administrator login.   

That should do it. I hope!
Sorry bout the confusion, I did not read your post right the first time.

Leo

---

### Post by rob_peer on 2008-03-09
sorry
what i meant was:
i have a router that needs a password.
this password, obviously, is saved in my keychain.
things work fine, as i can log in to gnome, which unlocks my keychain password.
but since its a desktop, id rather have automatic login.
but if i do that, i still have to manually unlock my keychain.

so, is there a way to have automatic login, that also unlocks my keychain, thus logging me in to my router?

---

