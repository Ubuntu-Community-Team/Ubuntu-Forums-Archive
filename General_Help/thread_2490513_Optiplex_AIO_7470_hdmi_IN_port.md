---
title: "Optiplex AIO 7470 hdmi IN port"
date: 2023-09-06
forum: General Help
---

### Post by midugre on 2023-09-06
I have an DELL Optiplex AIO 7470 with dual boot (Win11, Ubundu 22.04)
I'd like to use the HDMI IN port to display from a MINI PC  that has no monitor.
My desktop has a button to swicth from Internal display to HDMI IN.

It works well if using Win11, but doesn't work with Ubuntu.
Would appreciate any help. Thanks

---

### Post by Holger_Gehrke on 2023-09-06
You might have some luck with ddccontrol (command line - scriptable) or gddccontrol (graphical) depending on the way the display is internally connected to the rest of the system.

I use these programs to switch my external display between HDMI1 (raspberry pi 4) and HDMI2 (laptop).

You might need to use elevated privileges to use these programs since they directly access an i2c bus that is 'hidden' in most modern display connections and is called DDC (Display Data Channel for data going from the display to a device; used for transmitting EDID to devices so they know the available modes and resolutions) or DDC/CI (Display Data Channel/Command Interface for commands from a device to the display; makes most of the functions available from a Displays onboard menu available for programmatic use).

```

ddccontrol -p

```
will search for connected displays and output an overview of the parameters you can control on any displays found by using something like
```

ddccontrol dev:/dev/i2c-1 -r 0x60 -w 23

```
(this would write 23 to register hexadecimal 60 (the output of register addresses produced by 'ddcontrol -p' gives register addresses in hex but you can also uses decimal addresses), thereby switching my display to use HDMI1 as active input)

These programs can be found in the packages ddccontrol and gddccontrol and can be installed using apt or synaptic.

Holger

---

### Post by midugre on 2023-09-06
sudo ddccontrol -p

ddccontrol, version 0.6.0
Copyright 2004-2005 Oleg I. Vdovikin (oleg@cs.msu.su)
Copyright 2004-2006 Nicolas Boichat (nicolas@boichat.ch)
Ce programme est livré SANS AUCUNE GARANTIE.
Vous pouvez redistribuer des copies de ce programme sous les termes de la licence générale publique de GNU (GNU General Public License).


Moniteurs détectés :
 - Périphérique : dev:/dev/i2c-2
   DDC/CI supporté : Non
   Nom du moniteur : VESA standard monitor
   Type d'entrée : digitale
[COLOR=#ff0000]Pas de moniteur supportant le DDC/CI disponible.[/COLOR]
Vérifiez que les modules du noyau sont chargés (i2c-dev, et votre driver de "framebuffer"), si votre carte graphique en a besoin.

---

### Post by Holger_Gehrke on 2023-09-06
Well, so much for that idea ...

Holger

---

