---
title: "Odd Skype issue"
date: 2015-12-17
forum: General Help
---

### Post by cscj01 on 2015-12-17
I have a friend running running Ubuntu 14.04.3 x64 and Skype 4.3.  At first, everything worked.  Then, for some reason, problems arose.  I checked on the forums for him and began to try some things.  Some of the things I did (not specifically in the order listed) are:

[LIST]
[*]Completely remove Skype and reinstalled;
[*]Checked all PulseAudio settings for sound levels;
[*]Checked alsamixer for sound levels;
[*]Installed skype4pidgin.
[/LIST]
The problems we had at first were

[LIST]
[*]We had video but no sound from his contact, and his contact could not hear or see us;
[*] We could not hear the Echo/Sound Test;
[*]We then had video but no sound from his contact, and his contact could not hear us but could see us;
[*]We then had video but no sound from his contact, and his contact could hear us and could see us.
[/LIST]
The last item in the problem list is where we are now.  In addition, we still cannot hear the Echo/Sound test.  The second problem changed to the third problem after we installed skype4pidgin.

The only reason I can think of for the change after installing skype4pidgin is that some libraries may have been installed that were not there before.

So it seems to me that there is something involving audio that is not configured correctly.  We have checked PulseAudio and alsamixer, and they both show that all inputs and outputs are configured correctly.  Every other program (VLC, Audacity, Videos in Firefox, etc.) have no audio issues.

I also have Ubuntu 14.04.3 x64.  Even though I do not have a webcam, I installed Skype and skype4pidgin.  I have no issues with the Echio/Sound Test.  Obviously, I have no way of checking the video.  Is there something else we should check?  Thanks.

---

### Post by Habitual on 2015-12-17
You may wish to nuke ~/.Skype and try again.
You must quit/exit skype first before removing.

---

### Post by cscj01 on 2015-12-17
> **Habitual said:**
> You may wish to nuke ~/.Skype and try again.
You must quit/exit skype first before removing.
We have actually tried that to no avail.

I was wondering if there are any files that contain information for Skype to use while running.  I notice there are a number of .db files in~/.Skype/<username>.  Is there a way to query these databases?  I also notice there are a couple of XML files.  Should there be something specific to audio of which I should be aware in these XML files?

---

### Post by Habitual on 2015-12-18
> **cscj01 said:**
> Is there a way to query these databases?The ~/.Skype/<Identity>/main.db is the responsible 'db' for all convos in Skype.
[Skyperious]("https://suurjaak.github.io/Skyperious/") can read it easily.

---

