---
title: "fam problem"
date: 2005-10-14
forum: General Help
---

### Post by rutulian on 2005-10-14
I have a new Breezy box that is experiencing some FAM-related problem. When I login at the gdm screen, it takes a while for the desktop to show up, and then there is an error: "FAMOpen() failed, install fam/gamin". Well, gamin is installed on this machine.

If I check the .xsession-errors, it says:
```
(process:4630): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (10000)

(process:4628): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (10000)
Failed to connect to socket /tmp/fam--

```

I know what the problem is here. I'm using nss_winbind to authenticate against a Windows domain controller. It does id mapping between Windows SIDs and Unix UIDs. So UID 10000 is not a user in /etc/passwd, but is a mapped user from a Windows domain. This works fine for every other utility I use, but apparently gamin doesn't like it. Does anybody know if this is a bug in gamin? Or is there a quick fix that I haven't been able to figure out?

---

### Post by Sockies on 2005-11-02
I am having the same problem, but with virtual users and Courier-imap.

```
imapd-ssl: Failed to connect to socket /tmp/fam-- 
```

Everything works, but this causes a serious performance issue.  It takes forever to load messages in a mail client.

---

### Post by DavidGoodwin on 2005-12-23
Creating a local user with the appropriate uid fixed the problem for me, when setting up courier/pgsql/postfix.

---

