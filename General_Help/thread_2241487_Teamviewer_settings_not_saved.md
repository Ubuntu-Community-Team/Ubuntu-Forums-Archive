---
title: "Teamviewer settings not saved"
date: 2014-08-26
forum: General Help
---

### Post by fizikz on 2014-08-26
Since upgrading to 14.04, Teamviewer9 settings have reverted, and keep reverting, to defaults. If I change settings (such as not to show the "computers and connections" window on startup, or adjusting the microphone noise threshold, etc) the settings remain in effect for that session, but again revert to defaults after I quit Teamviewer and restart it.

I have the most recent version currently available for linux (v9.0.30203) and I have followed the instructions [here]("http://askubuntu.com/questions/419605/teamviewer-9-ubuntu-13-10-sound") to get sound working.

---

### Post by fizikz on 2014-09-04
I contacted TeamViewer support and actually got a response and solution:

> We got some news from our developers that this is unfortunately a known problem in the current version. Our developers are already working on a solution and this will be fixed as soon as possible.

As a workaround for you:
The problem here is, that if the file
/home/$USER/.config/teamviewer9/config/client.conf

is missing, TeamViewer will not create it, as it should.

Therefore, creating this file manually should resolve the issue, without having to wait for the next update.

The following command should do that:

touch /home/$USER/.config/teamviewer9/config/client.conf


---

### Post by octius4u on 2014-09-08
This worked for my Ubuntu 14.04 x64 Desktop with Teamviewer 9 Multiarch. Thanks for the solution.

---

### Post by wfwoo on 2015-01-26
> **fizikz said:**
> I contacted TeamViewer support and actually got a response and solution:

The work around is confirm working. Thank you.

---

