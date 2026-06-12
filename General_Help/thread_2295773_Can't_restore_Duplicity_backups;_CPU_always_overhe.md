---
title: "Can't restore Duplicity backups; CPU always overheats"
date: 2015-09-21
forum: General Help
---

### Post by jeremybmerrill2 on 2015-09-21
I just reinstalled 15.04 on a Lenovo Thinkpad x220.

Whenever I go to restore my backups from Duplicity, the CPU overheats and I get booted out to the login screen. Duplicity always makes it through the "preparing" stage, but restores few files (so far, dot-files/dot-folders up thru ".m"). 

I've tried installing all the power-saving utils I can find: thermald, tlp, indicator-cpufreq, etc. I've added a bunch of i915-related kernel config variables to grub. But no luck.

Lemme know if lsmod or lspci output would be helpful or anything like that. Might it be relevant that the partition I'm restoring from is encrypted with LUKS?

---

### Post by tgalati4 on 2015-09-21
Welcome to the forums.  Try taking a can of compressed air and blowing out the air vents.  If your fan is clogged, then that can create an a overtemperature situation.  Try installing *thinkfan* and look at your fan speeds.

Perhaps 15.04 is too much for an X220?

---

### Post by jeremybmerrill2 on 2015-09-21
Thanks, tgalati4! I'll see about getting some compressed air, that's not a bad idea.

I had 15.04 running mostly okay. It was having some issues with coming back from sleep and maybe video card stuff, so I figured I'd do a clean install. That is to say, during some periods of time, 15.04 ran great on my current hardware.

I'm trying to install 14.04 LTS, just in case that helps. We'll see! (New username, not new to Ubuntu. Been here since 6.06... :D )

---

### Post by tgalati4 on 2015-09-21
Welcome back then.  Thinkpads have always had thermal issues.  Either the fans are not big enough or the heat sinks are not big enough.  My T43p has 9 thermal sensors.  They don't put them in because they are bored.

Sometimes you can change the thermal shutdown triggers in BIOS.  Don't go too aggressive.  70C is usually the default, but you can push 75C or 80C.  Most chips are toast at 100 to 110C.

The X220 came with a large selection of processors.  What do you have?

```
cat /proc/cpuinfo
```

Some hints for Ubuntu configuration:  [http://www.thinkwiki.org/wiki/Category:X220](http://www.thinkwiki.org/wiki/Category:X220)

After getting your system set up, run a stress test to make sure your computer can run full speed at 100% CPU load.

```
sudo apt-get install cpuburn
```

Then run it multiple times, depending on how many cores you have:

```
burnP6 &
burnP6 &
sudo killall burnP6

```

Install some temperature displays on your panel and watch the temps rise.  If you get a thermal shutdown after a few minutes, then you have a cooling problem.  Your system should be able to run several minutes to several hours at 100% load.

Understand that the X-series thinkpads were designed to be light and thus are compromised with handling heat.

---

### Post by jeremybmerrill2 on 2015-09-21
I'll try that stuff out shortly, @tgalati4, thanks!

I ended up being able to successfully restore my system using the `duplicity` command in a GUI-less shell session. (Whatever you call it when you log out and then do Ctrl-Alt-F1 thru -F6), something like `duplicity file:///media/my_username/my_external_hdd/ /home/my_username/temp` and then copying all the stuff back into my actual home folder. Perhaps this will be useful to someone else.

Copying files over was quick, though the computer was running kind of hot. Either running on the command line kept the CPU from overheating... or I just fried my processor.

 I ordered some compressed air just to be safe.

---

### Post by tgalati4 on 2015-09-21
Understand that most Thinkpads have the GPU and CPU share the same heatsink.  So when the GPU gets hot, the CPU gets hot as well.  Running the terminal (console, command line) means you are not running the GPU in high-resolution mode, so it will run cooler.  That's a clever way to work around this problem--at least temporarily.

Install *lm-sensors* and look at your temperatures.

```
sudo apt-get install lm-sensors
sudo sensors-detect     (answer Yes to all questions)
reboot
sensors
```

---

### Post by jeremybmerrill2 on 2015-09-28
@tmgalati4: Thanks. I was able to use cpu-burn to peg the CPU at 100% (on all 4 cores) for a little bit. Strangely, temperature spiked to 94°C for a few seconds, then dropped and stayed at 84°C. (So, I never had any weird log outs or anything.)

This all is after cleaning the fans with compressed air. My suspicion still is that there might be a problem with Deja-Dup for pegging the CPU like it does on restore, but I'm... not going to test it.

Anyways, thanks for the help.

---

### Post by tgalati4 on 2015-09-28
84C is toasty.  Perhaps it is time to replace the heat sink paste on the CPU and GPU.  Or perhaps you have a broken screw holding down the heat sink.  Has the computer been dropped lately?

Using a good-quality ceramic or silver paste will reduce your temps 10C.  A broken screw or clip on the heat sink means it doesn't stay flat on the CPU die and it will get toasty quickly.

---

