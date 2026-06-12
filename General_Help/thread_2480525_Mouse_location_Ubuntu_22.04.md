---
title: "Mouse location Ubuntu 22.04"
date: 2022-11-01
forum: General Help
---

### Post by Robbyx on 2022-11-01
With mouse location set to on, I have read that I should be able to highlight the cursor location with Win key + K, but it does not work. I looked into the Ubuntu  shortcuts and there was no such setting. How do I revive it?

I am using the Xorg option not wayland.

---

### Post by Dennis N on 2022-11-01
It's the left control key that locates the cursor hot spot. It has to first be enabled in Settings > Accesibility

---

### Post by Robbyx on 2022-11-01
The locate pointer is on, in accessibility. None of these combinations work:

Left CTRL + ( K or WinKey)
Is there something else I can try?

---

### Post by MAFoElffen on 2022-11-01
The same setting is
```

gsettings get org.gnome.desktop.interface locate-pointer

```
You are wanting it set to true. If false, you can change it to true via
```

gsettings set org.gnome.desktop.interface locate-pointer true

```
Then, the left control key will find the cursor.

---

### Post by Dennis N on 2022-11-01
> **Robbyx said:**
> The locate pointer is on, in accessibility. None of these combinations work:

Left CTRL + ( K or WinKey)
Is there something else I can try?

The "locator" is really hard to see. Just a small solid circle that flashes once very quickly at the cursor hot spot. Press key again to repeat. It's not a very good locator in my opinion.

---

### Post by MAFoElffen on 2022-11-01
If you reset the cursor size from it's default of "24" to something like "36", and the above (locate-pointer) is set to "true"... Then when you use the left control key, it will show 3 blinking rings around the cursor, instead of one small ring. (Easier to find.)

Those two settings compliment each other.

---

### Post by Robbyx on 2022-11-01
Thank you, I can now see some change but it is very small and not at obvious. Is there a way to make the signal stronger? At present the very tip of the cursor does some minor change. If I keep pressing the key long enough there is some indication of pink it the tip, but it hardly noticeable.

---

### Post by MAFoElffen on 2022-11-01
Like I said
```

gsetting set or.gnome.desktop.interface cursor-size 36

```
Will make the cursor slightly larger... But also the "show-cursor" will be more exaggerated...

---

### Post by Dennis N on 2022-11-01
I experimented with this a bit using Ubuntu 22.04, and don't see any change to the flashing circle size with a larger size cursor. 

Tested:
**DMZ-white **set to 48 px (the max for this cursor)
**Yaru** set to 52 px

No rings either. But I have seen the expanding rings in some releases in the past - not sure which though.

Summary: Not a feature that is well done - at least in Ubuntu 22.04 and 22.10.

@MAFoElffen;
are you using Ubuntu 22.04?

---

### Post by MAFoElffen on 2022-11-02
@Dennis N -

Now, most of my machines are 22.04, but I stay about 50/50 in Gnome & i3... I still have lots of VM test machines in 16.04 thru 23.04, in various flavors.

I tested those settings in Gnome...

---

### Post by jamesspam on 2023-06-06
Might be a bit old, but I had the same problem. The solution is to also Set "Enable  animations" in the seeing menu. Then the visualization will actually be useful.

---

### Post by jamesspam on 2023-06-06
[COLOR=#000000]Might be a bit old, but I had the same problem with the actual vizualization. The solution is to also Set "Enable animations" in the seeing sub category. Then the visualization will actually be as described.[/COLOR]

---

### Post by Robbyx on 2023-06-16
Thank you.

---

