---
title: "Uninstalling Xine"
date: 2005-08-13
forum: General Help
---

### Post by Holdem on 2005-08-13
I had Totem working fine with wmv files sound and all. I then wanted a plugin for FF and installed Mplayer and Xine but Xine seems to of messed up wmv files.
I followed instructions on [http://www.frankandjacq.com/ubuntuguide/5.04/#xine-ui](http://www.frankandjacq.com/ubuntuguide/5.04/#xine-ui)
How do I roll back these commands:
```

gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "xine dvd://"
sudo rm -f /usr/share/applnk/Multimedia/xine.desktop
sudo ln -fs /usr/share/xine/desktop/xine.desktop /usr/share/applications/
sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup
sudo sed -e 's/totem.desktop/xine.desktop/g' /usr/share/applications/defaults.list_backup > /tmp/defaults.list
sudo mv /tmp/defaults.list /usr/share/applications/defaults.list
```

Should I just unistall Xine?

---

