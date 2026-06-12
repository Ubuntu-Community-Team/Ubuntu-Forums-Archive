---
title: "Imon vfd lirc--double touch"
date: 2008-02-15
forum: General Help
---

### Post by dablitz on 2008-02-15
I have Kubuntu 7.10 and compiled lirc 0.8.2 with no issues. I have the lirc running and mythtv works with it. but my problem is this. my system is receiveing a double tap with every remote button touch. so with an irw if I hit channel+ only once I get 2 commands to the system.


is there a way I can fix this.


# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.2(default) on Tue Feb 12 19:36:29 2008
#
# contributed by 
#
# brand:                       /etc/lirc/lircd.conf
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  /etc/lirc/lircd.conf
  bits           24
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  post_data_bits  8
  post_data      0xB7
  gap          235998
  toggle_bit_mask 0x4000

      begin codes
          rec                      0x298115
          play                     0x2A8115
          rew                      0x2A8195
          pause                    0x2A9115
          ffwd                     0x2B8115
          stop                     0x2B9715
          up                       0x299115
          down                     0x28A195
          right                    0x28B715
          left                     0x2B8195
          esc                      0x2BB715
          enter                    0x2AB195
          guide                    0x2A9395
          vol+                     0x28A395
          vol-                     0x28A595
          chan+                    0x289395
          chan-                    0x288795
          mute                     0x2B9595
          1                        0x28B595
          2                        0x2BB195
          3                        0x28B195
          4                        0x2A8595
          5                        0x299595
          6                        0x2AA595
          7                        0x2B9395
          8                        0x2A8515
          9                        0x2AA115
          0                        0x2BA595
      end codes

end remote




/etc/lirc# irw
00000000289395b7 00 chan+ /etc/lirc/lircd.conf
00000000289395b7 00 chan+ /etc/lirc/lircd.conf
00000000289395b7 00 chan+ /etc/lirc/lircd.conf
00000000289395b7 00 chan+ /etc/lirc/lircd.conf
00000000289395b7 00 chan+ /etc/lirc/lircd.conf
00000000289395b7 00 chan+ /etc/lirc/lircd.conf
00000000288795b7 00 chan- /etc/lirc/lircd.conf
00000000288795b7 00 chan- /etc/lirc/lircd.conf
0000000028a595b7 00 vol- /etc/lirc/lircd.conf
0000000028a595b7 00 vol- /etc/lirc/lircd.conf
0000000028a395b7 00 vol+ /etc/lirc/lircd.conf
0000000028a395b7 00 vol+ /etc/lirc/lircd.conf

---

