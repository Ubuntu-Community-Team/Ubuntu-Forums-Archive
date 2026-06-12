---
title: "Gnome-Tweaks &quot;Show Desktop&quot; stopped working"
date: 2019-01-30
forum: General Help
---

### Post by 2CV67 on 2019-01-30
In 18.04 I used Gnome-Tweaks for several minor jobs, including putting a "Show Desktop" icon on the top panel.

Since 18.10, the icon is still there but no longer works.

Is this a known bug?
Is there a solution? (Apart from Ctrl+Supr+d)

Thanks!

---

### Post by Dennis N on 2019-01-30
Probably it needs updating by the maintainer to work in Gnome Shell 3.30. There are two extensions named "Show Desktop", and the User comment on user pages for these is that they doesn't work in Ubuntu 18.10. Maybe you can find an alternative.

[https://extensions.gnome.org/](https://extensions.gnome.org/)

---

### Post by 2CV67 on 2019-10-28
Still not working in 19.04....

---

### Post by 2CV67 on 2019-12-08
Well - I jumped through some more hoops & got there in the end!

First I removed the old "Show Desktop Button" gnome shell extension from my applications.

Next I tried a newer & different "Show Desktop Button" extension with confusingly the same name.
It didn't install correctly, doesn't show any icon & refuses to be removed, so I don't recommend trying it!

I saw several keyboard shortcuts which were supposed to achieve "Show Desktop", including:
- Ctrl+Alt+d
- Ctrl+Alt+D
- Super+d
- Super+D
but none worked.

Then I found that Ctrl+Super+d or Ctrl+Super+D did work.

That might have been enough, but I felt I would have trouble remembering the combination, so revisited some of the solutions I had previously tried with no success.

I again tried what Ji_m suggested here:
[http://ubuntuhandbook.org/index.php/2018/10/add-show-desktop-button-ubuntu-18-10-18-04/]("http://ubuntuhandbook.org/index.php/2018/10/add-show-desktop-button-ubuntu-18-10-18-04/")
but not surprisingly it failed as it simulates Super+d which doesn't work for me in 19.04.

So I very slightly modified Ji_m's method to simulate Ctrl+Super+d & that works perfectly.

For anybody else stuck like me, I will describe what worked for me, with many thanks to Ji_m!

1. Install "xdotool" - I used SynApt for that.

2. Create & open the "Show Desktop" shortcut in Terminal:
```
gedit ~/.local/share/applications/show-desktop.desktop
```

3. Paste in the following then save:
```
[Desktop Entry]
Type=Application
Name=Show Desktop
Icon=desktop
Exec=xdotool key --clearmodifiers Ctrl+Super+d
```

4. Application Menu > Search for "Show Desktop" > Add to favorites.

You then have a "Show Desktop" icon in the Dock which (for me in 19.04) works...

---

