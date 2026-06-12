---
title: "Speakers popping and annoying ringing or hissing sound"
date: 2014-12-25
forum: General Help
---

### Post by I.Bun.Tu on 2014-12-25
I am making an effort to clean up this thread and clarify what my issue is and how I have tried to solve it thus far to hopefully generate some response as it has been nearly two weeks and I have received nothing...

I am running Ubuntu 14.10 on a Lenovo Ideapad y410p

I was running since release without issue and then a few weeks ago I started experiencing an issue where, shortly after logging in, the speakers pop and then a high pitched ringing sound comes from them. The only way I have been able to get the ringing to go off is to have the sound settings open or a similar sound manager like PulseAudio Volume Control. As soon as I close the sound manager the speakers pop and the ringing comes back (well within 5-10 seconds).

The speakers pop whenever the ringing comes on or off (e.g., opening a sound manager causes the speakers to pop and the ringing to stop).

If I have headphones plugged in, I cannot get the ringing to stop no matter what.

I have tried googling the issue and the only resource I found was listed here:

[http://askubuntu.com/questions/160882/popping-noise-from-laptop-speakers](http://askubuntu.com/questions/160882/popping-noise-from-laptop-speakers)

I tried the first step to comment out the intel_audio_powersave line in /usr/lib/pm-utils/power.d/intel-audio-powersave and add a false line, but I am unable to complete the second step of editing /sys/module/snd_hda_intel/parameters/power_save or /sys/module/snd_hda_intel/parameters/power_save_controller because my system doesn't seem to want to let me edit those files.

I have tried editing them in 3 different ways with 3 different editors. I will describe the errors below

using gksu gedit I am able to open the files and change the values but cannot save them in gedit and get the following error:

Could not create a backup file while saving "/sys/module/snd_hda_intel/parameters/power_save"

Could not back up the old copy of the file before saving the new one. You can ignore this warning and save the file anyway, but if an error occurs while saving, you could lose the old copy of the file. Save anyway?

and every time I click save anyway, the same message appears and it will not let me edit the file. I have to close without saving. Online people have suggested unchecking the option in gedit preferences to create backups, which I did in a non-root instance of gedit but it is checked again in the root instance. If I try to uncheck it in the root instance of gedit it will not save the preference change. When I go back into my preferences it is checked again.

Now if I try gksu mousepad (my preferred editor anyway) I am not even able to open the file and get the following error:

Failed to open the document.

Failed to map /sys/module/snd_hda_intel/parameters/power_save' /sys/module/snd_hda_intel/parameters/power_save': mmap() failed: No such device.

And finally if I try to use sudo nano or sudoedit when I got to write out to the file after saving changes I get an error that says invalid argument. No numbers or codes or letters following that, just invalid argument.

So as best as I can tell by scouring the internet, this is the only proposed solution to the popping/ringing issue and I'm not sure how to edit the necessary files. Could anyone please help? Thank you.

---

### Post by I.Bun.Tu on 2015-01-06
So I started a new Ask Ubuntu question specifically about not being able to edit these files and found out there is a permissions issue with files in the /sys/ folder.

The question I linked to about speaker popping was updated with the following commands:

```

sudo sh -c 'echo 0 > /sys/module/snd_hda_intel/parameters/power_save'
sudo sh -c 'echo N > /sys/module/snd_hda_intel/parameters/power_save_controller'


```

And that is able to edit the files, but the proposed method for making the switch permanent does not work.

I used

```


sudo chmod -w /sys/module/snd_hda_intel/parameters/power_save
sudo chmod -w /sys/module/snd_hda_intel/parameters/power_save_controller


```

but after every restart when I check the contents of /sys/module/snd_hda_intel/parameters/power_save_controller the value is changed back to Y.

Any ideas guys?

---

### Post by I.Bun.Tu on 2015-01-14
Hello? How come it is so difficult to get help in the Ubuntu Forums? I feel pariahed. I have tried to maintain a positive attitude but it is really difficult when I am just ignored day after day, week after week.

I have a very VERY simple question. I am sure there are hundreds of people on the forums that can answer it.

I am trying to make changes to files in the /sys folder permanent. I believe the best way to do this is by removing write permissions.

```
sudo chmod -w /sys/module/snd_hda_intel/parameters/power_save_controller
```

has no effect on write permissions as when I use

```
sudo sh -c 'echo N > /sys/module/snd_hda_intel/parameters/power_save_controller'
```

to edit the power_save_controller file from Y to N, it shows Y again after every restart. I am just trying to make this change permanent. Can someone please help me?

---

### Post by Holger_Gehrke on 2015-01-16
> **I.Bun.Tu said:**
> 
The question I linked to about speaker popping was updated with the following commands:
```

sudo sh -c 'echo 0 > /sys/module/snd_hda_intel/parameters/power_save'
sudo sh -c 'echo N > /sys/module/snd_hda_intel/parameters/power_save_controller'

```

And that is able to edit the files, but the proposed method for making the switch permanent does not work.

I used
```

sudo chmod -w /sys/module/snd_hda_intel/parameters/power_save
sudo chmod -w /sys/module/snd_hda_intel/parameters/power_save_controller

```

but after every restart when I check the contents of /sys/module/snd_hda_intel/parameters/power_save_controller the value is changed back to Y.


'/sys/' is not a real file system, it's a virtual file system that gives access to kernel internals. Whatever changes you make there will not survive a reboot. You should put those two echo commands into some script that gets called during boot. I can't help you with that, I'm still on 12.04 and 14.04 has quite a few changes in the init system ...

---

### Post by I.Bun.Tu on 2015-01-19
Thank you, that was very helpful. I believe I can figure out how to make a script that runs on startup and stick the echo commands in there. I will post back and let you guys know how it goes

---

