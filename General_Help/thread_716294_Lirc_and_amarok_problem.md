---
title: "Lirc and amarok problem"
date: 2008-03-05
forum: General Help
---

### Post by Christopherius on 2008-03-05
I created my .lircexec file for amarok but the only buttons that dont work are the skip forward and skip backward ones. i can fast forward and rewind songs but cant skip them. im positive that i have the proper commands put in the file:

```
#Amarok

begin
 prog = irexec
 remote = Hauppauge_350
 button = Play
 config = dcop amarok player play
end

begin
 prog = irexec
 remote = Hauppauge_350
 button = Stop
 config = dcop amarok player stop
end

begin
 prog = irexec
 remote = Hauppauge_350
 button = Pause
 config = dcop amarok player playPause
end

begin
 prog = irexec
 remote = Hauppauge_350
 button = Vol-
 repeat = 1
 config = dcop amarok player volumeDown 
end

begin
 prog = irexec
 remote = Hauppauge_350
 button = Vol+
 repeat = 1
 config = dcop amarok player volumeUp
end

begin
 prog = irexec
 remote = Hauppauge_350
 button = Forward
 repeat = 3
 config = dcop amarok player seekRelative 5
end

begin
 prog = irexec
 remote = Hauppauge_350
 button = Rewind 
 repeat = 3
 config = dcop amarok player seekRelative -5
end

begin
 prog = irexec
 remote = Hauppauge_350
 button = Mute
 config = dcop amarok player mute
end

begin
 prog = irexec
 remote = Hauppauge_350
 button = SkipForward
 config = dcop amarok player next
end

begin
 prog = irexec
 remote = Hauppauge_350
 button = Replay
 config = dcop amarok player prev
end

begin
 prog = irexec
 remote = Hauppauge_350
 button = Full
 repeat = 3
 config = dcop amarok player showOSD
end
```

thanks in advance for any help

---

### Post by pointone on 2008-03-05
I was only able to get Amarok to work properly with my remote by using the "GNOME Multimedia Keys" plugin. My .lircrc just pointed to generic media button scripts, as in:

```
begin
    prog = irexec
    button = VolUp
    config = /etc/acpi/volupbtn.sh
end

begin
    prog = irexec
    button = VolDown
    config = /etc/acpi/voldownbtn.sh
end
```

... and so on, for about every useful script in "/etc/acpi/".

---

