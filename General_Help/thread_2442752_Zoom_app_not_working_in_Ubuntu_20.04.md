---
title: "Zoom app not working in Ubuntu 20.04"
date: 2020-05-07
forum: General Help
---

### Post by mizurdiaga on 2020-05-07
Hi all! I've installed the snap version, from Ubuntu Software Center, of the zoom app, but it does not run properly. When I run it, it appears the main window of the app for a second, but it shuts. Anybody knows how to fix this?

---

### Post by Perfect Storm on 2020-05-07
Hi,

Try start zoom through the terminal and post its output.

regards,

---

### Post by mizurdiaga on 2020-05-07
I run it through the terminal but I do not have any output. The situation is the same: the window app appears for a second and then shuts. I have installed zoom-client fom ubuntu software center. Do I have to install anything else maybe?

---

### Post by Perfect Storm on 2020-05-07
I hoped for some output. Well try with:
```
touch ~/.config/zoomus.conf
```

---

### Post by mizurdiaga on 2020-05-07
It does not work. And no output. See the attached image.

---

### Post by Perfect Storm on 2020-05-07
I'm not using ubuntu, so this is shot: Have you tried the package provided on their homepage? [https://zoom.us/download](https://zoom.us/download)
You should first uninstall the current zoom first.

---

### Post by Perfect Storm on 2020-05-07
If it fails, please contact zoom this way: [https://support.zoom.us/hc/en-us/articles/205817409-Troubleshooting-Log-for-Linux](https://support.zoom.us/hc/en-us/articles/205817409-Troubleshooting-Log-for-Linux)

---

### Post by mizurdiaga on 2020-05-07
I've tried this too and the same happens.

---

### Post by mizurdiaga on 2020-05-07
> **Artificial Intelligence said:**
> I'm not using ubuntu, so this is shot: Have you tried the package provided on their homepage? [https://zoom.us/download](https://zoom.us/download)
You should first uninstall the current zoom first.
I've tried this too, but the same happens.

---

### Post by mizurdiaga on 2020-05-07
> **Artificial Intelligence said:**
> If it fails, please contact zoom this way: [https://support.zoom.us/hc/en-us/articles/205817409-Troubleshooting-Log-for-Linux](https://support.zoom.us/hc/en-us/articles/205817409-Troubleshooting-Log-for-Linux)
I'll try that! Thanks!

---

### Post by Perfect Storm on 2020-05-07
Then you need to follow the last link I provided I'm afraid.

---

### Post by monkeybrain20122 on 2020-05-07
Get rid of the snap, download and install the .deb for Ubuntu from [here]("https://zoom.us/download"). I think snap has issues accessing peripheries such as your webcam.

BTW, zoom is banned for official use around the world for security reason, you may want to try a secure alternative such as [jitsi-meet]("https://meet.jit.si/").

---

### Post by ActionParsnip on 2020-05-07
If you install the deb using

```

sudo dpkg -i packagename.deb
sudo apt-get -f install

```

What is the output?

---

