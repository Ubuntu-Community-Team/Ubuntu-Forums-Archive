---
title: "Nagios CGI Access ERROR 404 - Object Not FOund"
date: 2007-02-07
forum: General Help
---

### Post by hariste on 2007-02-07
For the first time i install Nagios, it works fine. Just using the sample config file (localhost.cfg) i can access [http://localhost/nagios](http://localhost/nagios) finely.

But after using  NagiosQl to manage the configuration file, when i access CGI got crash with error 404 - Object Not Found.

The difference between two situations up there just the sum of config file that used.

But can't access CGI..

Need Help.. 

Thanks for your attention..

Here's my nagios.cfg part

# OBJECT CONFIGURATION FILE(S)
# This is the configuration file in which you define hosts, host
# groups, contacts, contact groups, services, etc.  I guess it would
# be better called an object definition file, but for historical
# reasons it isn't.  You can split object definitions into several
# different config files by using multiple cfg_file statements here.
# Nagios will read and process all the config files you define.
# This can be very useful if you want to keep command definitions 
# separate from host and contact definitions...

# Command definitions
#cfg_file=/nagios/etc/commands.cfg

# Host and service definitions for monitoring this machine
#cfg_file=/nagios/etc/localhost.cfg


# You can split other types of object definitions across several
# config files if you wish (as done here), or keep them all in a
# single config file.

cfg_file=/nagios/etc/checkcommands.cfg
cfg_file=/nagios/etc/misccommands.cfg

cfg_file=/nagios/etc/contactgroups.cfg
cfg_file=/nagios/etc/contacts.cfg
cfg_file=/nagios/etc/timeperiods.cfg

cfg_file=/nagios/etc/hostgroups.cfg
cfg_file=/nagios/etc/servicegroups.cfg

#cfg_file=/nagios/etc/dependencies.cfg
#cfg_file=/nagios/etc/escalations.cfg

cfg_dir=/nagios/etc/hosts
cfg_dir=/nagios/etc/services

---

