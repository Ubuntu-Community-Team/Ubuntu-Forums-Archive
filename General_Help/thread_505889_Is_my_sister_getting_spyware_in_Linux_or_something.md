---
title: "Is my sister getting spyware in Linux or something?"
date: 2007-07-20
forum: General Help
---

### Post by picpak on 2007-07-20
Ok, here's the deal. It's a deal suspiciously similar to problems a typical Windows user might have. Right after my sister did her usual updates (Firefox, Wine) she opened up Iceape and Google was set as her home page. She checked through her preferences, and her home page hadn't changed from there. She closed it and opened it again, and it opened the regular home page. She then closed it again. To check if anything malicious was running, she opened the System Monitor. Iceape opened up instead, the System Monitor slowly following after that.

She's going to try running Spybot under Wine, which I don't think will do anything, but you never know.

---

### Post by picpak on 2007-07-20
She's searching with Spybot, and she's got a result! It's C:\Windows\Web\Related.htm (which is probably .wine/drive_c/Windows/Web/Related.htm as she doesn't have Windows). The search isn't done yet, but I thought I'd just let you know this. No, not even Linux is safe when it comes to spyware. :(

---

### Post by cookies on 2007-07-20
A) A Wine virus won't do much
B) Is this your WINE Browser or your Linux browser ?

Don't worry. If it is a Wine virsu, just delete /home/USERNAME/**.**wine

The DOT makes it hidden

Oh and a .htm is an HTML file, it won't do much at all!

---

### Post by strabes on 2007-07-20
Not if you have wine installed. Sorry to hear that that happened to you. A simple "sudo aptitude purge wine" should get rid of that stuff though. As far as I know there's no way it can get out of the wine environment since there really aren't spyware apps for linux in the wild.

---

### Post by picpak on 2007-07-20
I know what an .htm file is, but think about it: is there any chance it could be changed to go to Google and set in Iceape? Iceape isn't being run in Wine, I don't think Iceape is even available for Windows. I think there's more to it than just deleting .wine.

---

### Post by kerry_s on 2007-07-20
> **picpak said:**
> Ok, here's the deal. It's a deal suspiciously similar to problems a typical Windows user might have. Right after my sister did her usual updates (Firefox, Wine) she opened up Iceape and Google was set as her home page. She checked through her preferences, and her home page hadn't changed from there. She closed it and opened it again, and it opened the regular home page. She then closed it again. To check if anything malicious was running, she opened the System Monitor. Iceape opened up instead, the System Monitor slowly following after that.

She's going to try running Spybot under Wine, which I don't think will do anything, but you never know.

Yes, it does that after a update, normally it would point you to the firefox site telling you have successfully updated, but ubuntu changed that. on the iceape & system monitor thing. my guess is she clicked it earlier and it just takes it's usual sweet time opening.
and iceape to. debian changed it because they changed the name.

---

### Post by picpak on 2007-07-20
> **kerry_s said:**
> Yes, it does that after a update, normally it would point you to the firefox site telling you have successfully updated, but ubuntu changed that.

But she never updated Iceape or opened Firefox!

> **kerry_s said:**
> on the iceape & system monitor thing. my guess is she clicked it earlier and it just takes it's usual sweet time opening.

Your guess is as good as mine; but she made certain it was closed.

---

