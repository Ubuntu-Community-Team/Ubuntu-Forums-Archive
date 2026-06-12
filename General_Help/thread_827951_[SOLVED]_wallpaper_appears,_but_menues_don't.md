---
title: "[SOLVED] wallpaper appears, but menues don't"
date: 2008-06-13
forum: General Help
---

### Post by Knuffle on 2008-06-13
I am still a newbie but I have had Ubuntu working beautifully for over a month now. Last night I shut down my laptop and when I rebooted this morning none of the menues were working.All that showes up is my wallpaper. Any help you can give will be appreciated. Thanks.

---

### Post by sancho panza on 2008-06-13
Are you able to get to a terminal (Ctrl+Alt+F1 to F6) ? Have you rebooted from there? Have you tried a reboot using the power switch?

---

### Post by scouser73 on 2008-06-13
I had the same problem, this was an error on my part though, I had deleted the Evolution mail client and with the files that were got rid of, one was the Ubuntu desktop. I only realised this after restarting my PC where only the wallpaper was on show.

---

### Post by joshsmith on 2008-06-13
if you have the problem like scouser, do what sancho says to get into terminal, login, then run
sudo apt-get install ubuntu-desktop

---

### Post by Knuffle on 2008-06-13
Thank you. It worked. Now, do you know how to get rid of Ekiga and Evolution Mail without re-deleting my desktop? I was also trying to make Mozilla Thunderbird my default mail program. Thanks again for all your help.

---

### Post by scouser73 on 2008-06-14
Yes, you can delete Ekiga and Evolution, just make sure that any associated files don't include the Ubuntu Desktop, if they do, then leave those particular files, and you can delete the others.

---

