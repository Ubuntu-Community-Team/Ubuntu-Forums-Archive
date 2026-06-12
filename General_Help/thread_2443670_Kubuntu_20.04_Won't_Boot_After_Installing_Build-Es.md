---
title: "Kubuntu 20.04 Won't Boot After Installing Build-Essential"
date: 2020-05-18
forum: General Help
---

### Post by metal450 on 2020-05-18
I've got a near-fresh Kubuntu 20.04 install.  I was going through  & getting everything setup, until it randomly failed to reboot.  I'm  using whole-disk LUKS encryption, including the boot partition (setup  per [https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPartition](https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPartition)).  The specific behavior is: I see the grub menu, select Kubuntu, enter my  LUKS password, it successfully unlocks, then just freezes at the "Dell"  logo.


  Thanks to btrfs & Timeshift, I was able to rollback & figure  out that it's installing build-essential that's causing it to break.   I've tested it several times: I reboot smoothly, I do nothing other than  

  sudo apt install build-essential
  I reboot again, and it fails.  When it's stuck on the Dell logo,  nothing is responsive - CapsLock light doesn't work, and no single key  on the keyboard reveals anything (Ctrl+Alt+Delete works). If I reboot into recovery, drop down to a root shell, and 

  apt remove build-essential; apt autoremove
  it still fails to boot.  The only way to get it running again is to  boot into a live USB & restore the btrfs snapshot from right before I  installed build-essential.  If I install build-essential again, it dies again.
    Because installing build-essential installs a  bunch of other dependencies too, I actually went through them all &  installed the dependencies explicitly, to see if it was one of them  that was breaking the boot process.  I have it down to just two:  build-essential itself, and dpkg-dev, which are co-dependent. So it's  absolutely one of those two packages, and nothing else.

  If I edit the grub options to remove "quiet"  & "splash," I can see that the final line of the boot process where  it got stuck was "Starting Detect the available GPUs and deal with any  system changes." The screen was flickering.  However, a rebooted a  second time & did the exact same thing - and that time it made it  PAST that line, and the final line was "Started Run anacron jobs." Third  try, the last line was "Started simple Desktop Display Manager." So it  seems to be inconsistent where it's getting stuck.

  If I boot to recovery, then continue boot,  it succeeds. It only fails if I boot directly/normally. Even if I remove  build-essential & dpkg-dev after the recovery boot, it still fails  to boot.

     

Any idea how I could fix this would be greatly appreciated.

---

### Post by metal450 on 2020-05-18
Solved by ***sudo ubuntu-drivers autoinstall***.  I still have no  idea why build-essential would randomly break my graphics drivers &  completely stop Ubuntu from booting (with no sane error message as a  hint) - but ~8 hours of lost time later, Ubuntu seems to be running  stable again.

---

