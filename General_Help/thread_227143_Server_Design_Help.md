---
title: "Server Design Help"
date: 2006-08-01
forum: General Help
---

### Post by drewdavis1 on 2006-08-01
Hello Everyone,

First off, let me say that I have just begun down my path of learning Linux. I have been a MS junkie for many years and have finally decided to learn of the "other side".

I am in the process of redoing my home network and I am trying to determine how best to create the back end. Here is what I'm looking for and if anyone has any advice, it would be greatly be appreciated! :p 

Single server back end that will function as a:
-File share for Media, Documents, Home Folders, etc.
-Centralized logins for both MS Clients (XP Pro) and for Linux.
-Be able to access a share on a MS Client from Linux and vice versa.
-Love to be able to emulate "Windows Media Connect" on server to stream music collection to XBOX 360 but will just configure it to stream from a MS Client.

The network will be about a 50/50 of Ubuntu and XP Pro clients but, pending how much i like it, my convert to 100% Linux eventually.

I know the obvious answer is just use Samba as a DC but I am very used to ADS and would like to explore the idea of LDAP. Any input?

---

### Post by Stormbringer on 2006-08-01
> **drewdavis1 said:**
> Single server back end that will function as a:
-File share for Media, Documents, Home Folders, etc.

Samba with appropriate shares would be the easiest way to accomplish that job.

> **drewdavis1 said:**
> -Centralized logins for both MS Clients (XP Pro) and for Linux.

Define "Centralized logins" --- are you referring to roaming profiles?

> **drewdavis1 said:**
> -Be able to access a share on a MS Client from Linux and vice versa.

Well ... either use the "Connect to server" in Gnome's places menu or mount the windows-share into place by using the command-line.

i.e.

mount -t smbfs \\SERVER\Share /media/WindozeShare -o username=your_username,password=your_password

You may need to install smbfs first ... this can be done by issueing:

sudo apt-get install smbfs

For the other way around you would need to setup samba on your Linux Desktops so that you can get access from Windows --- you may take a look at the howto that is linked in my signature.

> **drewdavis1 said:**
> - Love to be able to emulate "Windows Media Connect" on server to stream music collection to XBOX 360 but will just configure it to stream from a MS Client.

No idea about this one ... there are many threads around in the forum about this topic, but to my knowledge no one really got it to work.

However, with this I cannot be of any help as I don't have an XBox 360.

> **drewdavis1 said:**
> I know the obvious answer is just use Samba as a DC but I am very used to ADS and would like to explore the idea of LDAP. Any input?

Have a lot of fun ... I already fiddled around with the LDAP backend but never got the beast to work ... and even if you can get it to work: samba CAN NOT - I repeat: CAN NOT - act as Active Directory Controller; samba is a DC at best.


Now that we clarfied the basic questions, how can I be of further help?

Regards,
-Storm

---

