---
title: "Ubuntu Kiosk - Disable / Remove / Hide Dash?"
date: 2014-05-09
forum: General Help
---

### Post by mcvickj on 2014-05-09
Greetings.  I am in the process of setting up a kiosk machine using Ubuntu 14.04 LTS Desktop amd64.  I have everything setup the way I want it with the exception of Dash.  Is there a way to disable Dash from returning any results?  Or perhaps remove it from the Launcher?  If there was an option to remove / hide the Launcher and just put a few icons on the desktop for allowed applications that would be fine too.

---

### Post by grahammechanical on 2014-05-09
We can autohide the Launcher and make the icons smaller. In 14.04 we can make them so small as to be unusable on a touch screen (I guess). We can make the reveal sensitivity high so that it becomes very difficulty to reveal the Launcher. We do this in System Settings>Appearance.

That leaves the problem of keyboard shortcuts. You may find something to disable in System Settings>Keyboard. Putting icons on the desktop is not so easy anymore in Ubuntu. You may wish to use the Dash to hold application icons. We can set the Dash to reveal full screen. I assume that you are removing many unnecessary applications from this install. In System Settings>Security & Privacy>Files & Applications we can severely limit what appears in the Dash. This will change what appears in the Recently Used section of the Dash. Each scope in the Dash can be individually disabled by clicking on it in the Dash.

Regards.

---

### Post by monkeybrain20122 on 2014-05-09
You can sort of disable the dash, go to System Settings > Security and  Privacy > Files and Applications and exclude your whole root directory, that way the dash wouldn't log or show anything so it is practically disabled (of course you have to turn off online search too). Instead of putting launcher icons on the desktop the design is to put them on the dock.

But what would be the point of using Ubuntu if you disable/remove all unity features? It sounds like you should use another flavour.

---

