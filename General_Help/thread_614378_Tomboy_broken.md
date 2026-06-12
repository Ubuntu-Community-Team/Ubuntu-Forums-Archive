---
title: "Tomboy broken"
date: 2007-11-15
forum: General Help
---

### Post by Mose250 on 2007-11-15
Hi all, 
I'm running Gutsy, a relatively new install.  Tomboy stopped working shortly after I started using Gutsy (which, I'm happy to say, is the first Linux distro release that's kept me off of Windows full-time).  I would really like to use Tomboy, though - I've tried a couple of different releases, but Tomboy won't launch out of the menu (nothing happens). 

If I run Tomboy from a terminal, I get the same error messages.  Here they are:

If I open a terminal and type "tomboy"  I get this
```
[DEBUG]: NoteManager created with note path "/home/jon/.tomboy".
[INFO]: Initializing Mono.Addins
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.Tomboy

Unhandled Exception: System.NullReferenceException: A null value was found where an object instance was required.
  at Mono.Addins.Database.AddinDatabase.Repair (IProgressStatus monitor) [0x00000] 
  at Mono.Addins.AddinRegistry.Rebuild (IProgressStatus monitor) [0x00000] 
  at Tomboy.AddinManager.InitializeMonoAddins () [0x00000] 
  at Tomboy.AddinManager..ctor (System.String tomboy_conf_dir) [0x00000] 
  at Tomboy.NoteManager.CreateAddinManager () [0x00000] 
  at Tomboy.NoteManager..ctor (System.String directory, System.String backup_directory) [0x00000] 
  at Tomboy.NoteManager..ctor (System.String directory) [0x00000] 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] 

```

If I type tomboy --whatever (start-here, search, or any other option except for help), I get this:
```
[DEBUG]: Unable to connect to Tomboy remote control: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/bin/tomboy exited with status 1
```

I've tried a couple different versions of Tomboy and I've tried reinstalling some Mono packages, but I'm pretty lost at this point in time.  And the strange thing is, if I run "sudo tomboy" it starts up and sits in the tray.  Weird.

Any help greatly appreciated!

---

### Post by Mose250 on 2007-11-16
I fixed it, I think:

```

cd /home/username/.tomboy
sudo rm * -rf
rmdir /home/username/.tomboy

```

Tomboy started right up!

---

