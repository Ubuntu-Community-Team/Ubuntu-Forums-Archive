---
title: "ftdi-sio driver Help Required"
date: 2016-01-01
forum: General Help
---

### Post by Jarubell on 2016-01-01
I am told I need to add a new VID/PID pair for the ftdi-sio driver is to write the following to  /sys/bus/usb-serial/drivers/ftdi_sio/new_id:

# modprobe ftdi_sio 
# echo 0403 bd90 > /sys/bus/usb-serial/drivers/ftdi_sio/new_id

It's for a new usb device, but I don't know how to do it, is there anyone who could help me?

James

---

