---
title: "Evolution Hangs when I try to reply to email"
date: 2006-10-23
forum: General Help
---

### Post by dwinslow23 on 2006-10-23
I am running evolution 2.8.1 and when I click the reply, reply to all, or forward buttons evolution hangs.  Has anyone else had this problem?  Does anyone have any suggestions on what could be causing the problem?

---

### Post by dwinslow23 on 2006-10-23
Update:

I can forward email but not reply.

---

### Post by Watcher on 2006-11-05
Well, since I turned on my pc today I'm having the same problem. Email comes in and I can open en view it allright but replying just seems to crash Evolution ... This is really annoying ...

---

### Post by Watcher on 2006-11-06
I think I may have found the source. Do you have the option to sync with your buddy list turned on in your evolution preferences. I did and the following message poped up in a terminal when running evolution from there:

> bernard@Hyphomicrobium:~$ evolution
CalDAV Eplugin starting up ...

(evolution-2.8:22417): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.8:22417): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.8:22417): DEBUG: mailto URL command: evolution %s
** (evolution-2.8:22417): DEBUG: mailto URL program: evolution

(evolution-2.8:22417): e-utils-WARNING **: Cannot resolve symbol 'org_gnome_new_mail_config' in plugin '/usr/lib/evolution/2.8/plugins/liborg-gnome-new-mail-notify.so' (not exported?)
BBDB spinning up...
bbdb: Buddy list has changed since last sync.
bbdb: Synchronizing buddy list to contacts...
bbdb: Done syncing buddy list to contacts.

The buddy list syncing caused evolution to hang until it was done ... Gonna see if that does the trick :)

---

### Post by Watcher on 2006-11-06
It does :D Just be patient and let it hang until it resolves itself and then turn off that option in your preferences

---

### Post by Cirrocco on 2007-09-17
if you're using exchange OWA you may also want to set automatic contacts to save to 'contacts' instead of 'global address list' (which you may not have permission to do)

you can find this in: 
Edit -> Preferences.
Mail Preferences -> Automatic Contacts

---

### Post by hotani on 2007-10-19
I get one reply out of evolution-exchange before it hangs and I have to restart the application. Started it last time via terminal to get some output next time it bombs...

Ahhh, there it goes! *boom*


```

$> evolution
CalDAV Eplugin starting up ...
Loading Spamassasin as the default junk plugin
** (evolution:13143): DEBUG: mailto URL command: evolution %s
** (evolution:13143): DEBUG: mailto URL program: evolution
creating
fff

(evolution:13143): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
BBDB spinning up...

** (evolution:13143): WARNING **: bbdb: Failed to add new contact: EBookStatus returned 3

(evolution:13143): e-data-server-DEBUG: Loading categories from "/home/hotani/.evolution/categories.xml"
(evolution:13143): e-data-server-DEBUG: Loaded 29 categories

(evolution:13143): GLib-GObject-WARNING **: IA__g_object_weak_unref: couldn't find weak ref 0xb65c0c90(0x8684ec8)

(evolution:13143): GLib-GObject-WARNING **: IA__g_object_weak_unref: couldn't find weak ref 0xb65c0c90(0x8684ec8)

(evolution:13143): GLib-GObject-WARNING **: IA__g_object_weak_unref: couldn't find weak ref 0xb65c0c90(0x8684ec8)

(evolution:13143): GLib-GObject-WARNING **: IA__g_object_weak_unref: couldn't find weak ref 0xb65c0c90(0x8684ec8)

(evolution:13143): GLib-GObject-WARNING **: IA__g_object_weak_unref: couldn't find weak ref 0xb65c0c90(0x8684ec8)
the cur is 80
the cur is 79
the cur is 78
the cur is 77
the cur is 76
the cur is 75
the cur is 74

(evolution:13143): GLib-GObject-WARNING **: IA__g_object_weak_unref: couldn't find weak ref 0xb65c0c90(0x8684ec8)

(evolution:13143): GLib-GObject-WARNING **: IA__g_object_weak_unref: couldn't find weak ref 0xb65c0c90(0x8684ec8)

(evolution:13143): GLib-GObject-WARNING **: IA__g_object_weak_unref: couldn't find weak ref 0xb65c0c90(0x8684ec8)

```

---

### Post by hotani on 2007-10-19
there didn't seem to be an existing bug for this so I [added a new one](https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/154464).

I'm still waiting for someone to [answer my previous question](http://ubuntuforums.org/showthread.php?t=522366) regarding ANY ALTERNATIVE TO EVOLUTION for working with an exchange server. ](*,)

---

### Post by hotani on 2007-11-13
This is still not working. I tried reinstalling evolution, deleting my exchange account, completely reinstalling evolution-exchange, but still get the same behavior. I can reply to ONE message only. When I attempt to reply to a second, evolution has to be killed. I'm not sure what else to try here.

---

### Post by devilears on 2007-12-07
i'm running 2.12.1 and have the same problem   :-(

---

### Post by hotani on 2007-12-10
I finally resolved this issue by removing the ~/.gconf/apps/evolution directory, then reinstalling evolution. After setting up the account from scratch I no longer had the issue when replying to e-mails.

Apparently the option in Synaptic to "Completely remove" doesn't do what it should.

---

### Post by gerstle on 2008-01-10
i was able to reply but not reply-all.  This seems to have helped a bit:

1. Remove the global Catalog Server Name
2. restart evolution
3. test reply-all feature
4. Put global catalog server name back in place
5. restart evolution
6. test reply-all feature -> woohoo!
7. drink more coffee.

casey g.

---

### Post by awyatt on 2008-01-29
> **gerstle said:**
> i was able to reply but not reply-all.  This seems to have helped a bit:

1. Remove the global Catalog Server Name
2. restart evolution
3. test reply-all feature
4. Put global catalog server name back in place
5. restart evolution
6. test reply-all feature -> woohoo!
7. drink more coffee.

casey g.

How do I remove "global Catalog Server Name" ?

---

### Post by pau13 on 2008-02-18
gconf-editor
In  "apps / evolution / autocontacts"
Change the "addressbook_source" to file:///home/username/.evolution/addressbook/local/system

---

