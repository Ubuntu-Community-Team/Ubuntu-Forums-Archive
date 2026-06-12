---
title: "SNMP Configuration problem - able to snmp outbound, unable to snmp inbound."
date: 2015-04-26
forum: General Help
---

### Post by wannbenixdude on 2015-04-26
I have a virtual lab setup. All elements using 192.168.0.0/16 (Actually 192.168.110.0/24, 192.168.47.0/24, 192.168.159.0/24, 192.168.44.0/24). One router, two Linux servers. One Ubuntu 14.04, one Centos 7. 

I am trying to setup snmp. 

I am able to snmpwalk  the router from both servers. 
I am able to snmpwalk the Centos server from the Ubuntu server. 
I am NOT able to snmpwalk the Ubuntu server from the Centos server. 
I am able to ping and ssh from the Centos server to the Ubuntu server and vice versa.

If Ive read and understand correctly, snmpd is the config info for the daemon or "server" side of snmp setup. 
And snmp.conf is the config info for the "agent" side of the snmp setup. 

If I got it right, then I have a problem somewhere with snmpd. 
I am also unable to use this syntax. ....Specifically the ending keyword. 

snmpwalk -v2c -c public 192.168.159.3 uptime
snmpwak -v2c -c public 192.168.159.3 system 

I would appreciate any help. Ive been working on this for a couple of days  ](*,)](*,)](*,) and just can see whats going on. I also have been unable to find any doc that explains step by step how to (basically) setup snmp, net-snmp etc etc.

 > 
/etc/default/snmpd
# This file controls the activity of snmpd and snmptrapd

# Don't load any MIBs by default.
# You might comment this lines once you have the MIBs downloaded.
export MIBS=/usr/share/mibs

# snmpd control (yes means start daemon).
SNMPDRUN=yes

# snmpd options (use syslog, close stdin/out/err).
#SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -g snmp -I -smux,mteTrigger,mteTriggerConf -p /var/run/snmpd.pid'
SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -g snmp -I -smux -p /var/run/snmpd.pid'

# snmptrapd control (yes means start daemon).  As of net-snmp version
# 5.0, master agentx support must be enabled in snmpd before snmptrapd
# can be run.  See snmpd.conf(5) for how to do this.
TRAPDRUN=no

# snmptrapd options (use syslog).
TRAPDOPTS='-Lsd -p /var/run/snmptrapd.pid'


> 
/etc/snmp/snmp.conf
mibs :


> 
/etc/snmp/snmpd.conf
###########################################################################
#
# snmpd.conf
#
#   - created by the snmpconf configuration program
#
###########################################################################
# SECTION: Monitor Various Aspects of the Running Host
#
#   The following check up on various aspects of a host.

# proc: Check for processes that should be running.
#     proc NAME [MAX=0] [MIN=0]
#   
#     NAME:  the name of the process to check for.  It must match
#            exactly (ie, http will not find httpd processes).
#     MAX:   the maximum number allowed to be running.  Defaults to 0.
#     MIN:   the minimum number to be running.  Defaults to 0.
#   
#   The results are reported in the prTable section of the UCD-SNMP-MIB tree
#   Special Case:  When the min and max numbers are both 0, it assumes
#   you want a max of infinity and a min of 1.

proc  mountd
proc  ntalkd    4
proc  sendmail 10 1

# disk: Check for disk space usage of a partition.
#   The agent can check the amount of available disk space, and make
#   sure it is above a set limit.  
#   
#    disk PATH [MIN=100000]
#   
#    PATH:  mount path to the disk in question.
#    MIN:   Disks with space below this value will have the Mib's errorFlag set.
#           Can be a raw integer value (units of kB) or a percentage followed by the %
#           symbol.  Default value = 100000.
#   
#   The results are reported in the dskTable section of the UCD-SNMP-MIB tree

disk       /     10000
disk       /var  5%

# load: Check for unreasonable load average values.
#   Watch the load average levels on the machine.
#   
#    load [1MAX=12.0] [5MAX=12.0] [15MAX=12.0]
#   
#    1MAX:   If the 1 minute load average is above this limit at query
#            time, the errorFlag will be set.
#    5MAX:   Similar, but for 5 min average.
#    15MAX:  Similar, but for 15 min average.
#   
#   The results are reported in the laTable section of the UCD-SNMP-MIB tree

load   12 10 5



###########################################################################
# SECTION: System Information Setup
#
#   This section defines some of the information reported in
#   the "system" mib group in the mibII tree.

# syslocation: The [typically physical] location of the system.
#   Note that setting this value here means that when trying to
#   perform an snmp SET operation to the sysLocation.0 variable will make
#   the agent return the "notWritable" error code.  IE, including
#   this token in the snmpd.conf file will disable write access to
#   the variable.
#   arguments:  location_string

#sysLocation    Sitting on the Dock of the Bay
syslocation  "Ubuntu VM"

# syscontact: The contact information for the administrator
#   Note that setting this value here means that when trying to
#   perform an snmp SET operation to the sysContact.0 variable will make
#   the agent return the "notWritable" error code.  IE, including
#   this token in the snmpd.conf file will disable write access to
#   the variable.
#   arguments:  contact_string

#sysContact     Me <me@example.org>
syscontact  "DONT CALL ME"

# sysservices: The proper value for the sysServices object.
#   arguments:  sysservices_number

sysServices    72
sysservices 76



###########################################################################
# SECTION: Agent Operating Mode
#
#   This section defines how the agent will operate when it
#   is running.

# master: Should the agent operate as a master agent or not.
#   Currently, the only supported master agent type for this token
#   is "agentx".
#   
#   arguments: (on|yes|agentx|all|off|no)

 master          agentx

# agentaddress: The IP address and port number that the agent will listen on.
#   By default the agent listens to any and all traffic from any
#   interface on the default SNMP port (161).  This allows you to
#   specify which address, interface, transport type and port(s) that you
#   want the agent to listen on.  Multiple definitions of this token
#   are concatenated together (using ':'s).
#   arguments: [transport:]port[@interface/address],...

#agentAddress  udp:127.0.0.1:161
agentAddress  udp:161






###########################################################################
# SECTION: Access Control Setup
#
#   This section defines who is allowed to talk to your running
#   snmp agent.

# rouser: a SNMPv3 read-only user
#   arguments:  user [noauth|auth|priv] [restriction_oid]

# rouser   authOnlyUser
#rouser          internalUser

# rocommunity: a SNMPv1/SNMPv2c read-only access community name
#   arguments:  community [default|hostname|network/bits] [oid]

#rocommunity public  default    -V systemonly
rocommunity public 192.168.0.0/16 

# rwcommunity: a SNMPv1/SNMPv2c read-write access community name
#   arguments:  community [default|hostname|network/bits] [oid]

rwcommunity  private  192.168.0.0/16



###########################################################################
# SECTION: Trap Destinations
#
#   Here we define who the agent will send traps to.

# trapsink: A SNMPv1 trap receiver
#   arguments: host [community] [portnum]

# trapsink     localhost public



#
# Unknown directives read in from other files by snmpconf
#
view   systemonly  included   .1.3.6.1.2.1.1
view   systemonly  included   .1.3.6.1.2.1.25.1
includeAllDisks  10%
iquerySecName   internalUser       
defaultMonitors          yes
linkUpDownNotifications  yes
 extend    test1   /bin/echo  Hello, world!
 extend-sh test2   echo Hello, world! ; echo Hi there ; exit 35





---

