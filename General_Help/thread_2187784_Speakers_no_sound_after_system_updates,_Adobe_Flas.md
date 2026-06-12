---
title: "Speakers no sound after system updates, Adobe Flash Player install"
date: 2013-11-13
forum: General Help
---

### Post by Xinghao_Chen on 2013-11-13
I just installed 12.04 64-bit on my ThinkPad T400. The install started from a DVD disk which was made from the AMD64 ISO download file. After the initial install (with network disabled), tests in System Setting -> Sound showed that both the right and left speakers did work (both announced the female voice) and the mic was working (the meter was moving up when I made some noises).

I then proceeded with enabling the wireless connection and system updates, which took sometime to complete, until a fresh system update check (after reboot) saying no new system updates.


(1) At this time, tests in System Settings -> Sound no longer produce any sound, even though the control panels and buttons show the speakers are on; (test of the mic still shows meter activities). It seems that the last batch of system updates disabled the speakers. How do I go about correcting this? (Just to make sure that the speakers do work, I booted the T400 with Windows Vista and both speakers work just fine.) 

(2) Opened the Firefox browser at [www.cbs.com]("http://www.cbs.com") and trying to play a video, it says need to install Adobe Flash Player; clicked on the Adobe button and proceeded to install, it came with three choices: YUM for Linux, a zip for other Linux, a .rmp for other Linux. I have no idea what these three mean and tried the YUM link. It then asked which application to use (for download?) so I used whatever the default was in there, which just downloaded and placed some files on ./etc but didn't seem to have installed anything. How do I go about install the Adobe Flash Player?

I am sorry if these may sound silly, but I have no clue as how to resolve these two issues. Well, I am a Ubuntu newbie.

Thank you in advance for pointers and advices.

---

### Post by Dreamer Fithp Apprentice on 2013-11-16
First of all, those are 2 totally seperate issues. It is just happenstance that you got both at about the same time. 

For the sound problem:
Try installing pavucontrol. Look at the output devices tab. There is a mute toggle there. Try that. Also try the volume settings there. There is also facility for selecting the correct hardware if for instance you have both onboard sound and a sound card. I don't know if it is the answer in your case but it often works for me.

For Adobe:
Try installing flashplugin-installer. It may need a reboot, I forget. I think you can delete the file you downloaded. It's not doing anything, just sitting inerlty in etc taking up space.

---

### Post by Xinghao_Chen on 2013-11-16
Thank you for your reply.

For the first paragraph in your reply, I agree. I am sorry if my problem-description appears to be any confusing. But they did came up after the 148 system updates and this newbie doesn't know which ones caused/triggered each problem.


For the second paragraph, how do I go about installing pavucontrol (and what does it do)?  Looking for it in the software store? My ThinkPad T400 laptop has what originally equipped from manufacture and there has been no other internal cards added. In the Vista's device manager it shows only one audio adaptor. I recall looked over all the control panels/tabs/buttons associated with speaker and audio and tried every available "click" - they just don't do anything in bringing back speakers "to make noise" (I should be clear that I did not reboot Ubuntu after changes made in the audio/speaker control tab/panels as I recall changes in these replaces are instantaneous).

For the third paragraph on Adobe, which flashplugin-installer to use and how do I go about it? My problem was the firefox was asking for Adobe Flash Player and I clicked the button/link in its window to install, thinking it would just like one does in the Windows and an Adobe Flash Player install window would pop up and so forth and the rest would be simple even with this newbie ... but it didn't.

Here is the current status: I have rebuilt Ubuntu 12.04 64-bit with the same DVD install disk but halted all system updates - the system has all from the amd64 ISO and nothing else. The installment works great and everything (sound, speaker, wifi, firefox, etc.) seems in the best working condition. There are 148 system updates waiting in the queue and I am thinking about what to do with them - I want the system to be secure (some of the system updates look like security updates) but at the same time I don't want to go through the above mentioned experience with silent speakers and the dead install of Adobe Flash Player for firefox. If I only know which system updates in the queue caused/might have caused the mentioned problems, I could just deselect them from installing system updates and move on. Then, this newbie doesn't know and have no clue. This is what I am struggling now.

Thank you for the time and patience.

---

### Post by Xinghao_Chen on 2013-11-17
Well, I did not know how to fix these two problems so I made a fresh re-install using the same ISO DVD disk followed by system updates. All seem to work fine now.

---

### Post by Dreamer Fithp Apprentice on 2013-11-24
Glad you're up and running and up to date. 

For the record and the benefit of those hypothetical future readers you install a package by either opening a package manager like software center or synaptic and searching for the package name and clicking the obvious buttons, etc. Or more easily, open a terminal and type ```
sudo apt-get install example-package-name
```And then press the [enter] key. So, in this case ```
sudo apt-get install pavucontrol
```And then press the [enter] key. And then type ```
sudo apt-get install flashplugin-installer
```And then press the [enter] key. Or even easier, run the two commands together like this ```
sudo apt-get install pavucontrol flashplugin-installer
```And then press the [enter] key.

---

