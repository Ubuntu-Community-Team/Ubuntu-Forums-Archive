---
title: "Firestarter pb -- ppp0 is not ready"
date: 2006-09-28
forum: General Help
---

### Post by FuzZy2006 on 2006-09-28
I have just changed my internet connection from one with a Ethernet cable (without modem) using pppoe and requiring a user and a pass; to one using an ADSL modem - it gets the IP using DHCP. The pb is that when I want to configure firestarter: ```
sudo firestarter
``` it gives me an error at the beggining that sais: ```
the device ppp0 is not ready. pls check your network device settings and make sure your internet connection is active. 
``` I can configure it but it says that it is disabled. What can I do?

---

### Post by wieman01 on 2006-09-28
1. Go to: Edit->Preferences->(Firewall)Network Settings->Detected Device(s) 
2. Choose your device (cable modem or similar)
3. Press "Accept"
4. Press "Start Firewall"

That's it. See screenshot.

---

### Post by tajmox on 2006-10-17
This didn't work for me.
My device is up, I used ifconfig -a to check.

---

### Post by Ferio on 2006-10-29
I'm having exactly the same problem, any idea anyone?

---

