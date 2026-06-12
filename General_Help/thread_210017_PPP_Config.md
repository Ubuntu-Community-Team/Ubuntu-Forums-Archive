---
title: "PPP Config"
date: 2006-07-06
forum: General Help
---

### Post by cssutto on 2006-07-06
I have installed a Kyocera PC card to connect to Alltel wirelss.

I finallyhave the card recognized and can dial out and get a connection.

However, I can not get a connection with my browser or my evolution.

What am I missing?

Here is the log:

Jul  6 02:15:52 localhost gconfd (root-24991): Exiting
Jul  6 02:16:05 localhost chat[328]: ATDT#777^M^M
Jul  6 02:16:05 localhost chat[328]: CONNECT
Jul  6 02:16:05 localhost chat[328]:  -- got it
Jul  6 02:16:05 localhost chat[328]: send (\d)
Jul  6 02:16:06 localhost pppd[327]: Serial connection established.
Jul  6 02:16:06 localhost pppd[327]: Using interface ppp0
Jul  6 02:16:06 localhost pppd[327]: Connect: ppp0 <--> /dev/ttyUSB0
Jul  6 02:16:08 localhost pppd[327]: CHAP authentication succeeded
Jul  6 02:16:08 localhost pppd[327]: CHAP authentication succeeded
Jul  6 02:16:09 localhost pppd[327]: local  IP address 166.165.214.147
Jul  6 02:16:09 localhost pppd[327]: remote IP address 71.28.103.18
Jul  6 02:16:09 localhost kernel: [17181142.548000] Inbound IN=ppp0 OUT= MAC= SRC=71.28.103.18 DST=255.255.255.255 LEN=54 TOS=0x00 PREC=0x00 TTL=1 ID=8040 PROTO=ICMP TYPE=9 CODE=0
Jul  6 02:16:09 localhost kernel: [17181142.748000] Inbound IN=ppp0 OUT= MAC= SRC=71.28.103.18 DST=255.255.255.255 LEN=54 TOS=0x00 PREC=0x00 TTL=1 ID=8051 PROTO=ICMP TYPE=9 CODE=0
Jul  6 02:16:09 localhost kernel: [17181142.948000] Inbound IN=ppp0 OUT= MAC= SRC=71.28.103.18 DST=255.255.255.255 LEN=54 TOS=0x00 PREC=0x00 TTL=1 ID=8058 PROTO=ICMP TYPE=9 CODE=0
Jul  6 02:16:32 localhost gconfd (root-738): starting (version 2.14.0), pid 738 user 'root'
Jul  6 02:16:32 localhost gconfd (root-738): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul  6 02:16:32 localhost gconfd (root-738): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jul  6 02:16:32 localhost gconfd (root-738): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul  6 02:16:32 localhost gconfd (root-738): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul  6 02:16:32 localhost gconfd (root-738): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul  6 02:19:32 localhost gconfd (root-738): GConf server is not in use, shutting down.
Jul  6 02:19:32 localhost gconfd (root-738): Exiting
Jul  6 02:20:02 localhost pppd[327]: Terminating on signal 15
Jul  6 02:20:02 localhost pppd[327]: Connect time 3.9 minutes.
Jul  6 02:20:02 localhost pppd[327]: Sent 8320 bytes, received 8524 bytes.
Jul  6 02:20:02 localhost pppd[327]: Connection terminated.
Jul  6 02:20:02 localhost pppd[327]: Exit.

---

### Post by kripkenstein on 2006-07-06
I'm no expert, but in my experience such symptoms are related to the card not being well-supported under linux.

But, you say you tried a browser and Evolution. How about ping (e.g. 64.233.187.99, Google), host (e.g. google.com)?

---

### Post by cssutto on 2006-07-06
Cananyone tell me what the garbage in this log means?

 6 08:45:00 localhost chat[13900]: abort on (BUSY)
Jul  6 08:45:00 localhost chat[13900]: abort on (NO CARRIER)
Jul  6 08:45:00 localhost chat[13900]: abort on (VOICE)
Jul  6 08:45:00 localhost chat[13900]: abort on (NO DIALTONE)
Jul  6 08:45:00 localhost chat[13900]: abort on (NO DIAL TONE)
Jul  6 08:45:00 localhost chat[13900]: abort on (NO ANSWER)
Jul  6 08:45:00 localhost chat[13900]: abort on (DELAYED)
Jul  6 08:45:00 localhost chat[13900]: send (ATZ^M)
Jul  6 08:45:00 localhost chat[13900]: expect (OK)
Jul  6 08:45:09 localhost chat[13900]: ~^?}#@!}!}!} }5}"}&} } } } }#}%B#}%}%}&#}0}8Dq}.~~^?}#@!}!}"} }5}"}&} } } } }#}%B#
Jul  6 08:45:13 localhost chat[13900]: }%}%}&#}0}8D}:g~~^?}#@!}!}#} }5}"}&} } } } }#}%B#}%}%}&#}0}8DL8~~^?}#@!}!}$} }5}"}
Jul  6 08:45:17 localhost chat[13900]: &} } } } }#}%B#}%}%}&#}0}8DL4~~^?}#@!}!}%} }5}"}&} } } } }#}%B#}%}%}&#}0}8D}:k~~^?
Jul  6 08:45:19 localhost chat[13900]: }#@!}!}&} }5}"}&} } } } }#}%B#}%}%}&#}0}8Dq}"~~^?}#@!}!}'} }5}"}&} } } } }#}%B#}%
Jul  6 08:45:23 localhost chat[13900]: }%}&#}0}8D']~~^?}#@!}!}(} }5}"}&} } } } }#}%B#}%}%}&#}0}8Dq};~~^?}#@!}!})} }5}"}&}
Jul  6 08:45:27 localhost chat[13900]:  } } } }#}%B#}%}%}&#}0}8D'D~~^?}#@!}!}*} }5}"}&} } } } }#}%B#}%}%}&#}0}8DL-~~^?}#@
Jul  6 08:45:45 localhost chat[13900]: alarm
Jul  6 08:45:45 localhost chat[13900]: send (AT^M)
Jul  6 08:45:45 localhost chat[13900]: expect (OK)
Jul  6 08:45:55 localhost chat[13900]: ~^?}#@!}!}!} }5}"}&} } } } }#}%B#}%}%}&#}0Nb&E~~^?}#@!}!}"} }5}"}&} } } } }#}%B#}%
Jul  6 08:45:59 localhost chat[13900]: }%}&#}0NbM,~~^?}#@!}!}#} }5}"}&} } } } }#}%B#}%}%}&#}0Nb};s~~^?}#@!}!}$} }5}"}&} }
Jul  6 08:46:03 localhost chat[13900]:  } } }#}%B#}%}%}&#}0Nb};}_~~^?}#@!}!}%} }5}"}&} } } } }#}%B#}%}%}&#}0NbM ~~^?}#@!}
Jul  6 08:46:05 localhost chat[13900]: !}&} }5}"}&} } } } }#}%B#}%}%}&#}0Nb&I~~^?}#@!}!}'} }5}"}&} } } } }#}%B#}%}%}&#}0
Jul  6 08:46:09 localhost chat[13900]: Nbp}6~~^?}#@!}!}(} }5}"}&} } } } }#}%B#}%}%}&#}0Nb&P~~^?}#@!}!})} }5}"}&} } } } }#
Jul  6 08:46:13 localhost chat[13900]: }%B#}%}%}&#}0Nbp}/~~^?}#@!}!}*} }5}"}&} } } } }#}%B#}%}%}&#}0Nb};f~~^?}#@!}%}*} }$
Jul  6 08:46:30 localhost chat[13900]: alarm
Jul  6 08:46:30 localhost chat[13900]: Failed
Jul  6 08:46:31 localhost pppd[13898]: Exit.

---

### Post by cssutto on 2006-07-06
I seem to have solved the problem, with a couple of exceptions.

The biggest problem now is that everytime I reboot, which is often with a laptop on the move, pon tells me that there is an unknown device ttyUSB0.

So I have to enter the command  sudo modprobe usbserial vendor=0xc88 product=0x17da

every time that I boot.

Why is this not sticking?

How do I get it to stick?

What seems to be a minor problem is that the above command line should have a maxSize option.

Apparently the maxSize command is not longer available in Dapper.

Or has it been replaced by something else?

CSSJR

---

### Post by hallert on 2006-07-28
this is because modprobe only inserts the module into the currently running kernel. It dosn't edit the start up configs to tell the kernel to load it at boot. (ie is temporary). To get it to insert the module at every boot edit the modules config file in the /etc/ folder. that should do it.

---

