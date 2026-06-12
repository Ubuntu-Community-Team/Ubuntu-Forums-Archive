---
title: "Unable to connect bluetooth headset"
date: 2022-08-13
forum: General Help
---

### Post by helionism on 2022-08-13
I'm failing connect my WH-1000XM4v headset on 22.04

When I check the status of the bluetooth service I get this

```

bluetoothd[877]: src/service.c:btd_service_connect() a2dp-sink profile connect failed for XXXXXXXXXX: Protocol not available

``` 

Any ideas? Let me know if there is any more info you would want.

---

### Post by helionism on 2022-08-13
Just after posted this I have fixed it by finding and following the suggestion posted here

[https://askubuntu.com/questions/1172000/a2dp-sink-profile-connect-failed](https://askubuntu.com/questions/1172000/a2dp-sink-profile-connect-failed)

sudo apt-get install pulseaudio-module-bluetooth
sudo killall pulseaudio
pulseaudio --start    
sudo systemctl restart bluetooth

---

