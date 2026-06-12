---
title: "Error in Immutable Page at wiki.ubuntu.com"
date: 2024-03-18
forum: General Help
---

### Post by 0cs935-bill on 2024-03-18
On page : [https://wiki.ubuntu.com/DebuggingBluetooth](https://wiki.ubuntu.com/DebuggingBluetooth) in the section titled : **On Ubuntu Desktop**, the sed commands recommended will mess up the files.


The change for bluetooth should be limited to the following line only: 
ExecStart=/usr/lib/bluetooth/bluetoothd
where -d is appropriate.


The change for pulseaudio should be limited only to the line:
ExecStart=/usr/bin/pulseaudio --daemonize=no –log-target=journal
where the recommended -d is an error and should be replaced by something like -vvvv to increase verbosity levels.

---

