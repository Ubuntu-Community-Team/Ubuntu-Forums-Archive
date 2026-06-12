---
title: "Midi not working in Java"
date: 2008-02-25
forum: General Help
---

### Post by Bontrey on 2008-02-25
> $ java MiniMiniMusicApp
javax.sound.midi.MidiUnavailableException
        at javax.sound.midi.MidiSystem.getDefaultDeviceWrapper(MidiSystem.java:1096)
        at javax.sound.midi.MidiSystem.getReceiver(MidiSystem.java:258)
        at javax.sound.midi.MidiSystem.getSequencer(MidiSystem.java:460)
        at javax.sound.midi.MidiSystem.getSequencer(MidiSystem.java:366)
        at MiniMiniMusicApp.play(MiniMiniMusicApp.java:12)
        at MiniMiniMusicApp.main(MiniMiniMusicApp.java:7)
Caused by: java.lang.IllegalArgumentException: Requested device not installed
        at javax.sound.midi.MidiSystem.getDefaultDevice(MidiSystem.java:1148)
        at javax.sound.midi.MidiSystem.getDefaultDeviceWrapper(MidiSystem.java:1094)
        ... 5 more

I typed in code from the Head First Java book and I get these exceptions... Maybe it's a problem with ice-tea... How do I switch between Java versions? I remember there was a command that lists all the versions of java installed and let you choose with numbers.

---

### Post by taurus on 2008-02-25
```
sudo update-alternatives --config java
```

---

