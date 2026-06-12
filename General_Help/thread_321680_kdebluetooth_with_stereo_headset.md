---
title: "kdebluetooth with stereo headset"
date: 2006-12-19
forum: General Help
---

### Post by raffalaser on 2006-12-19
hi all,

need help! i want to use my stereo headset jabra bluetooth with my laptop for skype use. i follow the wiki (looks pretty exactly my scope), and I suddenly discovered that i was not using any kde application to manage my bluetooth integrated in the laptop (HP pavillon 1000).

then I installed it and now if i launch in the terminal kbluetoothd i have:

raffa@raffa-laptop:~$ kbluetoothd
Link points to "/tmp/ksocket-raffa"
Link points to "/tmp/kde-raffa"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbluetoothd: HciListener::HciListener()
kbluetoothd: Using hci0 as default bluetooth device.
kbluetoothd: TrayIcon::slotMruMenuUpdate
kbluetoothd: TrayIcon::slotMruMenuUpdate
kbluetoothd: HciDevMonitor::slotTimeout(): Device found
kbluetoothd: HciListener::~HciListener()
kbluetoothd: HciListener::HciListener()

i quote only the beginning, couse it is a bit long.

while the terminal is running the output, i get the bluetooth icon popping up in the sistem tray on the right top corner (which is not working out any commands i give). Of course in the application menu i have no kbluetooth icon mentioned to click and run, 

i have no idea how to work this out.

pls give a hint!!](*,) 

ciao

---

