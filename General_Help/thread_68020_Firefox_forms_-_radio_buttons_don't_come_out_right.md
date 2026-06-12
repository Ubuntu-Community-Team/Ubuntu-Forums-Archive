---
title: "Firefox forms - radio buttons don't come out right"
date: 2005-09-21
forum: General Help
---

### Post by Steve Smith on 2005-09-21
I've run the "Automated setup" script from the Wiki ([https://wiki.ubuntu.com/RestrictedFormats)](https://wiki.ubuntu.com/RestrictedFormats)).  It's changed the Firefox forms to make them more Gnome-like, which I want to keep.  But it's screwed the radio buttons up: the unselected radio button is fine, but the selected one doesn't have a circle around it, it's just a blob.  Is there any way I can change that?

The relevent bit of the script that changed it is:
```
echo "Installing firefox forms"
cd /usr/lib/mozilla-firefox/
${wget} ${firefox_forms}
tar xvzf ff-forms.tar.gz
rm -f ff-forms.tar.gz
```

---

### Post by Steve Smith on 2005-09-24
I've worked out what it's done: it's changed some files in /usr/lib/mozilla-firefox/res.  I've made a new /usr/lib/mozilla-firefox/res/radio_checked.png, but it isn't quite right.

Is there anyone who hasn't changed their Firefox forms who could mail me that image if I PM you my address?

---

