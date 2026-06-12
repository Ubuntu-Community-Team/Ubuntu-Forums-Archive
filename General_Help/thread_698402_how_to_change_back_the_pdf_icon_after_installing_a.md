---
title: "how to change back the pdf icon after installing adobe reader 8"
date: 2008-02-16
forum: General Help
---

### Post by htor on 2008-02-16
copy paste this into the terminal:
```
for icon_size in 16 22 24 32 48 64 128; do
sudo xdg-icon-resource uninstall --novendor --context apps --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/AdobeReader8.png"
sudo xdg-icon-resource uninstall --novendor --context apps --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/adobe.pdf.png"
sudo xdg-icon-resource uninstall --novendor --context mimetypes --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/adobe.pdf.png" 'application-pdf'
sudo xdg-icon-resource uninstall --novendor --context apps --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.fdf.png"
sudo xdg-icon-resource uninstall --novendor --context mimetypes --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.fdf.png" 'application-fdf'
sudo xdg-icon-resource uninstall --novendor --context apps --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.adobe.pdx.png"
sudo xdg-icon-resource uninstall --novendor --context mimetypes --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.adobe.pdx.png" 'application-pdx'
sudo xdg-icon-resource uninstall --novendor --context apps --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.adobe.xdp+xml.png"
sudo xdg-icon-resource uninstall --novendor --context mimetypes --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.adobe.xdp+xml.png" 'application-xdp+xml'
sudo xdg-icon-resource uninstall --novendor --context apps --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.adobe.xfdf.png"
sudo xdg-icon-resource uninstall --novendor --context mimetypes --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.adobe.xfdf.png" 'application-xfdf'
done
```

---

### Post by htor on 2008-02-16
here:

> for icon_size in 16 22 24 32 48 64 128; do
sudo xdg-icon-resource uninstall --novendor --context apps --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/AdobeReader8.png"
sudo xdg-icon-resource uninstall --novendor --context apps --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/adobe.pdf.png"
sudo xdg-icon-resource uninstall --novendor --context mimetypes --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/adobe.pdf.png" 'application-pdf'
sudo xdg-icon-resource uninstall --novendor --context apps --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.fdf.png"
sudo xdg-icon-resource uninstall --novendor --context mimetypes --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.fdf.png" 'application-fdf'
sudo xdg-icon-resource uninstall --novendor --context apps --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.adobe.pdx.png"
sudo xdg-icon-resource uninstall --novendor --context mimetypes --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.adobe.pdx.png" 'application-pdx'
sudo xdg-icon-resource uninstall --novendor --context apps --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.adobe.xdp+xml.png"
sudo xdg-icon-resource uninstall --novendor --context mimetypes --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.adobe.xdp+xml.png" 'application-xdp+xml'
sudo xdg-icon-resource uninstall --novendor --context apps --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.adobe.xfdf.png"
sudo xdg-icon-resource uninstall --novendor --context mimetypes --size $icon_size "/opt/Adobe/Reader8/Resource/Icons/${icon_size}x${icon_size}/vnd.adobe.xfdf.png" 'application-xfdf'
done

---

### Post by K.Mandla on 2008-02-16
Moved to General Help.

---

### Post by K.Mandla on 2008-02-16
Moved to General Help. Similar threads merged.

---

