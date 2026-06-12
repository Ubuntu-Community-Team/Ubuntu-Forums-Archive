---
title: "Wireshark installed, how to run?!?!"
date: 2007-02-19
forum: General Help
---

### Post by Nectron on 2007-02-19
Hi All,

I've just installed wireshark, and used a ./configure, make, sudo make install
All seemed fine, and I got no errors, wireshark files are locacted at /usr/share/wireshark

But I still couldn't figure out how to run it!!

I know this might seem silly, but I've looked everywhere with no luck of knowing how to run it..

Any comment is welcome

---

### Post by Maestro23 on 2007-02-19
> **Nectron said:**
> Hi All,

I've just installed wireshark, and used a ./configure, make, sudo make install
All seemed fine, and I got no errors, wireshark files are locacted at /usr/share/wireshark

But I still couldn't figure out how to run it!!

I know this might seem silly, but I've looked everywhere with no luck of knowing how to run it..

Any comment is welcome

Quick google: 
[http://www.wireshark.org/docs/](http://www.wireshark.org/docs/)
[http://www.wireshark.org/docs/wsug_html/#ChCustCommandLine](http://www.wireshark.org/docs/wsug_html/#ChCustCommandLine)

---

### Post by Nectron on 2007-02-19
humm..

I tried the command "wireshark" but it says command not found! nothing seemed weird at the installation process..

There are also files for it at the /usr/local/share/wireshark

I don't know what went wrong, what do you suggest I should do ?

---

### Post by mikewhatever on 2007-02-19
Actually, wireshark is in the repositories and can be installed through synaptic. This way you do get an icon in the menu.

---

### Post by Maestro23 on 2007-02-19
Yeah, I would uninstall and d/l from the repositories. Installing some things from source can be be tricky if you are new to linux.

The OP can open a terminal and type:

> which wireshark

whereis wireshark

locate wireshark

Should see the path to the .bin file.

---

### Post by Nectron on 2007-02-19
Here's exactly what the installation left on my system, I looked for a .BIN file but there doesn't seem to be one. I guess installing from source wasn't a good idea.

```

/home/nectron/Desktop/Packages/wireshark-0.99.3a.tar.gz
/usr/local/lib/libwireshark.so.0.0.1
/usr/local/lib/libwireshark.so.0
/usr/local/lib/libwireshark.so
/usr/local/lib/libwireshark.la
/usr/local/lib/wireshark
/usr/local/lib/wireshark/plugins
/usr/local/lib/wireshark/plugins/0.99.5
/usr/local/lib/wireshark/plugins/0.99.5/agentx.so
/usr/local/lib/wireshark/plugins/0.99.5/agentx.la
/usr/local/lib/wireshark/plugins/0.99.5/artnet.so
/usr/local/lib/wireshark/plugins/0.99.5/artnet.la
/usr/local/lib/wireshark/plugins/0.99.5/asn1.so
/usr/local/lib/wireshark/plugins/0.99.5/asn1.la
/usr/local/lib/wireshark/plugins/0.99.5/ciscosm.so
/usr/local/lib/wireshark/plugins/0.99.5/ciscosm.la
/usr/local/lib/wireshark/plugins/0.99.5/docsis.so
/usr/local/lib/wireshark/plugins/0.99.5/docsis.la
/usr/local/lib/wireshark/plugins/0.99.5/enttec.so
/usr/local/lib/wireshark/plugins/0.99.5/enttec.la
/usr/local/lib/wireshark/plugins/0.99.5/cosnaming.so
/usr/local/lib/wireshark/plugins/0.99.5/cosnaming.la
/usr/local/lib/wireshark/plugins/0.99.5/coseventcomm.so
/usr/local/lib/wireshark/plugins/0.99.5/coseventcomm.la
/usr/local/lib/wireshark/plugins/0.99.5/tango.so
/usr/local/lib/wireshark/plugins/0.99.5/tango.la
/usr/local/lib/wireshark/plugins/0.99.5/parlay.so
/usr/local/lib/wireshark/plugins/0.99.5/parlay.la
/usr/local/lib/wireshark/plugins/0.99.5/gryphon.so
/usr/local/lib/wireshark/plugins/0.99.5/gryphon.la
/usr/local/lib/wireshark/plugins/0.99.5/h223.so
/usr/local/lib/wireshark/plugins/0.99.5/h223.la
/usr/local/lib/wireshark/plugins/0.99.5/irda.so
/usr/local/lib/wireshark/plugins/0.99.5/irda.la
/usr/local/lib/wireshark/plugins/0.99.5/lwres.so
/usr/local/lib/wireshark/plugins/0.99.5/lwres.la
/usr/local/lib/wireshark/plugins/0.99.5/mate.so
/usr/local/lib/wireshark/plugins/0.99.5/mate.la
/usr/local/lib/wireshark/plugins/0.99.5/megaco.so
/usr/local/lib/wireshark/plugins/0.99.5/megaco.la
/usr/local/lib/wireshark/plugins/0.99.5/mgcp.so
/usr/local/lib/wireshark/plugins/0.99.5/mgcp.la
/usr/local/lib/wireshark/plugins/0.99.5/opsi.so
/usr/local/lib/wireshark/plugins/0.99.5/opsi.la
/usr/local/lib/wireshark/plugins/0.99.5/pcli.so
/usr/local/lib/wireshark/plugins/0.99.5/pcli.la
/usr/local/lib/wireshark/plugins/0.99.5/profinet.so
/usr/local/lib/wireshark/plugins/0.99.5/profinet.la
/usr/local/lib/wireshark/plugins/0.99.5/rlm.so
/usr/local/lib/wireshark/plugins/0.99.5/rlm.la
/usr/local/lib/wireshark/plugins/0.99.5/rtnet.so
/usr/local/lib/wireshark/plugins/0.99.5/rtnet.la
/usr/local/lib/wireshark/plugins/0.99.5/rudp.so
/usr/local/lib/wireshark/plugins/0.99.5/rudp.la
/usr/local/lib/wireshark/plugins/0.99.5/sbus.so
/usr/local/lib/wireshark/plugins/0.99.5/sbus.la
/usr/local/lib/wireshark/plugins/0.99.5/stats_tree.so
/usr/local/lib/wireshark/plugins/0.99.5/stats_tree.la
/usr/local/lib/wireshark/plugins/0.99.5/v5ua.so
/usr/local/lib/wireshark/plugins/0.99.5/v5ua.la
/usr/local/share/man/man4/wireshark-filter.4
/usr/local/share/wireshark
/usr/local/share/wireshark/help
/usr/local/share/wireshark/help/toc
/usr/local/share/wireshark/help/getting_started.txt
/usr/local/share/wireshark/help/capturing.txt
/usr/local/share/wireshark/help/capture_filters.txt
/usr/local/share/wireshark/help/display_filters.txt
/usr/local/share/wireshark/help/faq.txt
/usr/local/share/wireshark/help/overview.txt
/usr/local/share/wireshark/diameter
/usr/local/share/wireshark/diameter/chargecontrol.xml
/usr/local/share/wireshark/diameter/dictionary.dtd
/usr/local/share/wireshark/diameter/dictionary.xml
/usr/local/share/wireshark/diameter/imscxdx.xml
/usr/local/share/wireshark/diameter/mobileipv4.xml
/usr/local/share/wireshark/diameter/nasreq.xml
/usr/local/share/wireshark/diameter/sip.xml
/usr/local/share/wireshark/diameter/sunping.xml
/usr/local/share/wireshark/diameter/TGPPSh.xml
/usr/local/share/wireshark/dtds
/usr/local/share/wireshark/dtds/dc.dtd
/usr/local/share/wireshark/dtds/itunes.dtd
/usr/local/share/wireshark/dtds/mscml.dtd
/usr/local/share/wireshark/dtds/pocsettings.dtd
/usr/local/share/wireshark/dtds/presence.dtd
/usr/local/share/wireshark/dtds/reginfo.dtd
/usr/local/share/wireshark/dtds/rlmi.dtd
/usr/local/share/wireshark/dtds/rss.dtd
/usr/local/share/wireshark/dtds/smil.dtd
/usr/local/share/wireshark/dtds/xcap-caps.dtd
/usr/local/share/wireshark/dtds/watcherinfo.dtd
/usr/local/share/wireshark/AUTHORS-SHORT
/usr/local/share/wireshark/COPYING
/usr/local/share/wireshark/manuf
/usr/local/share/wireshark/wireshark.html
/usr/local/share/wireshark/tshark.html
/usr/local/share/wireshark/wireshark-filter.html
/usr/local/share/wireshark/capinfos.html
/usr/local/share/wireshark/editcap.html
/usr/local/share/wireshark/idl2wrs.html
/usr/local/share/wireshark/mergecap.html
/usr/local/share/wireshark/text2pcap.html
/usr/local/share/wireshark/dumpcap.html
/usr/local/share/wireshark/cfilters
/usr/local/share/wireshark/colorfilters
/usr/local/share/wireshark/dfilters
/usr/local/share/wireshark/radius
/usr/local/share/wireshark/radius/dictionary
/usr/local/share/wireshark/radius/dictionary.3com
/usr/local/share/wireshark/radius/dictionary.3gpp
/usr/local/share/wireshark/radius/dictionary.3gpp2
/usr/local/share/wireshark/radius/dictionary.acc
/usr/local/share/wireshark/radius/dictionary.alcatel
/usr/local/share/wireshark/radius/dictionary.alteon
/usr/local/share/wireshark/radius/dictionary.altiga
/usr/local/share/wireshark/radius/dictionary.aptis
/usr/local/share/wireshark/radius/dictionary.ascend
/usr/local/share/wireshark/radius/dictionary.bay
/usr/local/share/wireshark/radius/dictionary.bintec
/usr/local/share/wireshark/radius/dictionary.bristol
/usr/local/share/wireshark/radius/dictionary.cablelabs
/usr/local/share/wireshark/radius/dictionary.cabletron
/usr/local/share/wireshark/radius/dictionary.cisco
/usr/local/share/wireshark/radius/dictionary.cisco.bbsm
/usr/local/share/wireshark/radius/dictionary.cisco.vpn3000
/usr/local/share/wireshark/radius/dictionary.cisco.vpn5000
/usr/local/share/wireshark/radius/dictionary.colubris
/usr/local/share/wireshark/radius/dictionary.columbia_university
/usr/local/share/wireshark/radius/dictionary.compat
/usr/local/share/wireshark/radius/dictionary.cosine
/usr/local/share/wireshark/radius/dictionary.ericsson
/usr/local/share/wireshark/radius/dictionary.erx
/usr/local/share/wireshark/radius/dictionary.extreme
/usr/local/share/wireshark/radius/dictionary.foundry
/usr/local/share/wireshark/radius/dictionary.freeradius
/usr/local/share/wireshark/radius/dictionary.gandalf
/usr/local/share/wireshark/radius/dictionary.garderos
/usr/local/share/wireshark/radius/dictionary.gemtek
/usr/local/share/wireshark/radius/dictionary.itk
/usr/local/share/wireshark/radius/dictionary.juniper
/usr/local/share/wireshark/radius/dictionary.karlnet
/usr/local/share/wireshark/radius/dictionary.livingston
/usr/local/share/wireshark/radius/dictionary.localweb
/usr/local/share/wireshark/radius/dictionary.merit
/usr/local/share/wireshark/radius/dictionary.microsoft
/usr/local/share/wireshark/radius/dictionary.mikrotik
/usr/local/share/wireshark/radius/dictionary.navini
/usr/local/share/wireshark/radius/dictionary.netscreen
/usr/local/share/wireshark/radius/dictionary.nokia
/usr/local/share/wireshark/radius/dictionary.nomadix
/usr/local/share/wireshark/radius/dictionary.propel
/usr/local/share/wireshark/radius/dictionary.quintum
/usr/local/share/wireshark/radius/dictionary.redback
/usr/local/share/wireshark/radius/dictionary.redcreek
/usr/local/share/wireshark/radius/dictionary.shasta
/usr/local/share/wireshark/radius/dictionary.shiva
/usr/local/share/wireshark/radius/dictionary.sonicwall
/usr/local/share/wireshark/radius/dictionary.springtide
/usr/local/share/wireshark/radius/dictionary.t_systems_nova
/usr/local/share/wireshark/radius/dictionary.telebit
/usr/local/share/wireshark/radius/dictionary.trapeze
/usr/local/share/wireshark/radius/dictionary.tunnel
/usr/local/share/wireshark/radius/dictionary.unisphere
/usr/local/share/wireshark/radius/dictionary.unix
/usr/local/share/wireshark/radius/dictionary.usr
/usr/local/share/wireshark/radius/dictionary.valemount
/usr/local/share/wireshark/radius/dictionary.versanet
/usr/local/share/wireshark/radius/dictionary.wispr
/usr/local/share/wireshark/radius/dictionary.xedia

```

- How can I uninstall it? "I installed from source"

- using apt-get didn't find wireshark, what's the dea?

I got all my network tools installed last night except wireshark and it's really important,

Thannks for the replies, and I hope we solve this in no time..

---

### Post by mikewhatever on 2007-02-19
> which wireshark

whereis wireshark

locate wireshark 

Maestro,
these are freaking useful, thank you.

---

