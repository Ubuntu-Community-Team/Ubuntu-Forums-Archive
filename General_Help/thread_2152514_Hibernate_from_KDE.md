---
title: "Hibernate from KDE"
date: 2013-06-08
forum: General Help
---

### Post by Jellby on 2013-06-08
Hi all,

After upgrading from 11.10 to 12.04 (yes, I know I'm a bit late), hibernation has stopped working from the KDE button. The button is enabled and I have created the famous /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pk1a file, so I guess that's not the problem.

What happens is that I click the hibernate button, I get the box asking if I want to hibernate, then the screen goes black, some notification appears at the bottom left and right corners (too fast to see, but they seem to have a green check mark), and that's all... If I now move the mouse, I'm asked for the password, so it's just a locked desktop. I can unlock and everything's fine.

Since I had tuxonice previously, I installed it again, but nothing's changed.

Anyway, "hibernate" or "pm-hibernate" work apparently flawlessly from the console, even from Konsole inside KDE. So I'm suspecting it's just the code linked to the hibernate button that's not working. How can I configure that? How can I "debug" this? I don't find anything in the logs (they only seem to have information about the successful hibernations/restores).

(And in case you wonder, hibernation is a must when you cannot have your laptop plugged and cannot rely on, or do not want to unnecessarily use, the battery. It takes some time to restore, but you have all your windows and documents open as they were.)

Thank you

---

### Post by Jellby on 2013-06-09
> **Jellby said:**
> The button is enabled and I have created the famous /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pk1a file, so I guess that's not the problem.

Sorry, user error. The file should be called "com.ubuntu.enable-hibernate.pkla", that's a letter ell, and not a number one, in the extension. Changed the name and it's working now.

I said the hibernate button was enabled... but that's only because I had the "lock & logout" applet in the panel. There was indeed no hibernate button in the kickoff logout menu (now there is).

---

