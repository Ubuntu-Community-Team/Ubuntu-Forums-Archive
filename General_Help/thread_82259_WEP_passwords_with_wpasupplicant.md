---
title: "WEP passwords with wpasupplicant"
date: 2005-10-26
forum: General Help
---

### Post by dcardamo on 2005-10-26
Hi,

I've got wpa supplicant working at home with two different WPA networks on my ipw2200 card.   The only problem that I have is that work uses WEP with WEP passwords and I haven't seen a configuration example for wpasupplicant on how to configure that.

Does anyone know?

Thanks,

Dan

---

### Post by dcardamo on 2005-10-28
No comments, but I found a work around myself.

I don't think wpa supplicant can support this so I found a script somewhere that I hooked in that lets me run wpa, wep, and wpa2 and it will automatically find a network to connect to.

You can find it on my site:
[http://www.hld.ca/archives/2005/10/27/automating-wireless-networks-between-wpa-and-wep-as-well-as-automatically-vpning-using-ssh/]("http://www.hld.ca/archives/2005/10/27/automating-wireless-networks-between-wpa-and-wep-as-well-as-automatically-vpning-using-ssh/")

---

### Post by thtde on 2005-10-29
It's also possibly with wpa_supplicant. You have to add this to its config file:

```
network={
        ssid="Your ESSID"
        key_mgmt=NONE
        wep_key0=Your WEP key
}

```

---

### Post by dcardamo on 2005-10-31
[QUOTE=thtde]It's also possibly with wpa_supplicant. You have to add this to its config file:

```
network={
        ssid="Your ESSID"
        key_mgmt=NONE
        wep_key0=Your WEP key
}

```[/QUOTE]

Do you know how to enter a wep password rather than just a hex key?

---

### Post by zencoder on 2005-11-11
[QUOTE=dcardamo]Do you know how to enter a wep password rather than just a hex key?[/QUOTE]

[http://www.speedguide.net/wlan_key.php](http://www.speedguide.net/wlan_key.php) should help you convert your password to HEX

---

