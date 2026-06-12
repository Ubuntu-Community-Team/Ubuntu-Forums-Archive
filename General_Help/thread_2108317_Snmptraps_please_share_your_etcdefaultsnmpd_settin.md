---
title: "Snmptraps please share your /etc/default/snmpd settings."
date: 2013-01-24
forum: General Help
---

### Post by la_bigmac on 2013-01-24
Snmptraps..


  I am going round in circles. After some pain, I can now get snmptranslate to pick up all of the MIBS downloaded via download-mibs. I shoved them all into one directory and pulled down a few more that were missing..


  Anyway coming back to my problem, the command below runs and outputs perfectly, OID are translated into human readable messages. YAY

  

snmptrapd -m +ALL -Lf /var/log/snmptrap.log --disableAuthorization=yes
  

-m +ALL = Load all the MIB found in MIBs path (net-snmp-config --default-mibdirs) shows the path.
  -Lf output to the following log. 
  disableAuthorization=yes Fairly obvious, the recent versions of snmptrap require authentication by default, I will enable that once I have it working!
  

Now, getting all this to survive a reboot, that is what is causing me pain. 
  I think I am correct in saying that service snmpd starts and stops both snmpd and snmptrapd. 
  

The “options” are configured in 
  /etc/default/snmpd  
  The options I want are the ones I have in the command above..
  export MIBS=/root/.snmp/mibs   <- location of all my mibs.
  TRAPDOPTS='-m +ALL -Lf /var/log/snmptrap.log -c /etc/snmp/snmptrapd.conf'
  

This runs and outputs to snmptrapd.conf, but does not translate OID to human readable form.
  

If you have this working, please share with me your /etc/default/snmpd settings.
  

Any help is most welcome. 
  [FONT=&quot]Mat. [/FONT]

---

### Post by la_bigmac on 2013-01-25
YAY I have it working!

 
  I had to edit /etc/default/snmpd and change the export options from export MIBS to export MIBDIRS 
   
  # export MIBS=/root/.snmp/mibs
  export MIBDIRS=/root/.snmp/mibs
   
  Hope this helps someone.

---

