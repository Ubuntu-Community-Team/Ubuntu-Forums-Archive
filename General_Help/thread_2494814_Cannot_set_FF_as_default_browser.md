---
title: "Cannot set FF as default browser"
date: 2024-01-27
forum: General Help
---

### Post by Norm24 on 2024-01-27
In the past I was using the Mozilla Build of FF installed thru the Ubuntuzilla PPA and had no issues setting it as the default browser either thru Control Center or FF settings.

On my current machine I am using Ubuntu Mate 22.04.3 and I am currently using the Flatpak install of FF as it would appear that Ubuntuzilla is no longer supported.I also have Chromium and Edge installed.After clicking on a link in an email I noticed Edge opened up instead of FF and after checking FF Setting I saw there was no option to set it as default so I then went into Preferred Applications in Control Center and the only two options given were Edge and Chromium.I also installed the Snap version of FF thinking possibly the Flatpak version was the issue but to no avail.

Any ideas on how to make the Flatpak/Snap installs default?

---

### Post by Norm24 on 2024-01-27
Was able to figure it out (for the Flatpak version) using this command:

```
xdg-settings set default-web-browser <your_flatpak_browser.desktop>
```

In my case the actual command:

```
xdg-settings set default-web-browser org.mozilla.firefox.desktop
```

To verify:

```
xdg-settings check default-web-browser org.mozilla.firefox.desktop
```

This fix won't add FF to the Preferred Applications list in Mate Control Center but if you have Gnome Control Center installed it will be added to the Default Applications list.

---

