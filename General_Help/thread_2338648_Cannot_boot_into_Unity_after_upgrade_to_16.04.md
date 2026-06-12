---
title: "Cannot boot into Unity after upgrade to 16.04"
date: 2016-09-30
forum: General Help
---

### Post by seeyouza on 2016-09-30
Hi all

Hope someone can help, this is driving me insane.

This morning I updated to 16.04 from 15.10.

The upgrade decided to upgrade mysql-server during the process, which failed. It then stated it would completely cancel the upgrade because mysql-server-5.7 installation failed, but then proceeded anyway and prompted me to reboot, which I did. Upon reboot, I was presented with the login screen and entered my password. The login prompt disappeared, the desktop showed up and then immediately flashed back to the login prompt again. If I pick Metacity from the login prompt instead of Unity, everything boots fine. However, logging out and back into Unity presents the same problem.

I then logged into a terminal and reinstalled my nvidia drivers, in case they were causing the failure. On reboot, I could log into Unity, but the desktop was completely devoid of anything. No top bar, no launcher, nothing. I can right click and open a terminal, which pops up in a window without borders, title bars or anything else. This has happened before (which is why I tried the driver re-install) and after some research I learned that I needed to re-enable the unity plugin via CCSM to fix the problem, which it did at that point in time. So I tried the same thing now, except that CCSM is not saving the changes. I enable Unity, everything seems fine, until I exit CCSM and then restart it to check if the changes persist, which they don't. If I click Preferences in CCSM which I've started from terminal, I see the following error (and preferences doesn't load):

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/ccm/Pages.py", line 1300, in ShowPreferences
    preferencesPage = PreferencesPage(self.Context)
  File "/usr/lib/python2.7/dist-packages/ccm/Pages.py", line 1153, in __init__
    self.PluginListPage = PluginListPage(context)
  File "/usr/lib/python2.7/dist-packages/ccm/Pages.py", line 1000, in __init__
    self.UpdateEnabledPluginsList()
  File "/usr/lib/python2.7/dist-packages/ccm/Pages.py", line 1041, in UpdateEnabledPluginsList
    activePlugins = self.Context.Plugins['core'].Screen['active_plugins'].Value
KeyError: 'active_plugins'

I'm not sure how to proceed at this point. Any help would be appreciated. While I could carry on using Metacity, I'd rather not.

---

### Post by seeyouza on 2016-09-30
Well after many hours, I apt-get purged compiz, ccsm, unity and ubuntu-desktop. I then manually deleted every trace of a compiz-related file from my drive, and re-installed those packages. Launching CCSM I was able to save after enabling the Unity plugin and upon reboot, could boot into Unity normally. Hope it saves someone a headache in future.

---

