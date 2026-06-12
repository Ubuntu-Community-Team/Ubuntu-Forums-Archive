---
title: "Bluetooth"
date: 2016-02-10
forum: General Help
---

### Post by leprechaun91 on 2016-02-10
I am trying to connect to a health device that communicates over SPP  from ubuntu 14.4 . I used rfcomm connect 0 and got a connection. And then send  data by using:

```
  echo -en '\xb0\x04\x00\x01\xa1\xf1\x93' > /dev/rfcomm0  

```But when i then open wireshark and check the traffic it sends the data  over L2CAP. So what do i have to change so i can communicate over SPP? output from /etc/bluetooth/rfcomm.conf:

  ```

rfcomm0 {
    bind no;
    device 8C:DE:52:A1:B1:9D;
    channel 6;
    comment "channel 6";}
     

```

---

