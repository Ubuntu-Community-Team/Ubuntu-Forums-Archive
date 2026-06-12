---
title: "ASE Express Edition need help"
date: 2005-08-12
forum: General Help
---

### Post by arlie on 2005-08-12
I installed ASE Express Edition and everything went fine until I got to the point of starting the server where I got an error: Unable to boot server 'VIRTUALX'. Below is the content of the log file:

Fri Aug 12 09:55:26 2005: srvbuild/12.5.3/P/Linux Intel/Linux 2.4.18-18.7.xsmp i686/EBF 12207/OPT/Sun Jan 23 21:19:25 PST 2005
Fri Aug 12 09:55:26 2005: Getting attribute values from sybinit resource file `/opt/sybase/ASE-12_5/sqlsrv.res'.
Fri Aug 12 09:55:26 2005:   
Fri Aug 12 09:55:26 2005: 
Fri Aug 12 09:55:26 2005: 
type = 1
server_page_size = 2k
master_device_physical_name = /opt/sybase/data/master.dat
master_device_size = 30
master_database_size = 6
sybsystemprocs_device_physical_name = /opt/sybase/data/sysprocs.dat
sybsystemprocs_device_size = 120
sybsystemprocs_database_size = 120
errorlog = /opt/sybase/ASE-12_5/install/VIRTUALX.log
configfile = /opt/sybase/ASE-12_5/VIRTUALX.cfg
sybsystemdb_device_physical_name = 
sybsystemdb_device_size = 5
sybsystemdb_database_size = 5
shmem = /opt/sybase/ASE-12_5
default_backup_server = VIRTUALX_BS
server_name = VIRTUALX
force_buildmaster = yes
Fri Aug 12 09:55:26 2005: (Shell command) /opt/sybase/ASE-12_5/bin/dataserver -d/opt/sybase/data/master.dat -b30M -z2k -sVIRTUALX -e/opt/sybase/ASE-12_5/install/VIRTUALX.log -T1623 -f > /tmp/sbruemuF 2>&1 
dataserver: master device size for this server: 30.0 Mb
dataserver: master database size for this server: 6.0 Mb
dataserver: model database size for this server: 2.0 Mb
00:00000:00000:2005/08/12 09:55:27.43 kernel  Adaptive Server Enterprise Express Edition (Limits: 1 Engine, 2GB Memory, 5GB Disk space).
00:00000:00000:2005/08/12 09:55:27.66 kernel  Using config area from primary master device.
00:00000:00000:2005/08/12 09:55:27.66 server  Configuration Error: Configuration file, '/opt/sybase/VIRTUALX.cfg', does not exist.
00:00000:00000:2005/08/12 09:55:27.66 kernel  Warning: A configuration file was not specified and the default file '/opt/sybase/VIRTUALX.cfg' does not exist. SQL Server creates the default file with the default configuration.
00:00000:00000:2005/08/12 09:55:27.69 kernel  Warning: Using default file '/opt/sybase/VIRTUALX.cfg' since a configuration file was not specified. Specify a configuration file name in the RUNSERVER file to avoid this message.
00:00000:00000:2005/08/12 09:55:27.71 kernel  os_create_region: can't allocate 41359360 bytes
00:00000:00000:2005/08/12 09:55:27.71 kernel  kbcreate: couldn't create kernel region.
00:00000:00000:2005/08/12 09:55:27.71 kernel  kistartup: could not create shared memory
Fri Aug 12 09:55:28 2005: Buildmaster return code: 0.
Fri Aug 12 09:55:28 2005: (Shell command) /opt/sybase/ASE-12_5/bin/dataserver -z2k -d/opt/sybase/data/master.dat -e/opt/sybase/ASE-12_5/install/VIRTUALX.log -c/opt/sybase/ASE-12_5/VIRTUALX.cfg -M/opt/sybase/ASE-12_5 -sVIRTUALX -T1623 > /dev/null 2>&1 
Fri Aug 12 09:58:38 2005: Unable to boot server 'VIRTUALX'.

---

### Post by arlie on 2005-08-12
[QUOTE=arlie]I installed ASE Express Edition and everything went fine until I got to the point of starting the server where I got an error: Unable to boot server 'VIRTUALX'. Below is the content of the log file:

Fri Aug 12 09:55:26 2005: srvbuild/12.5.3/P/Linux Intel/Linux 2.4.18-18.7.xsmp i686/EBF 12207/OPT/Sun Jan 23 21:19:25 PST 2005
Fri Aug 12 09:55:26 2005: Getting attribute values from sybinit resource file `/opt/sybase/ASE-12_5/sqlsrv.res'.
Fri Aug 12 09:55:26 2005:   
Fri Aug 12 09:55:26 2005: 
Fri Aug 12 09:55:26 2005: 
type = 1
server_page_size = 2k
master_device_physical_name = /opt/sybase/data/master.dat
master_device_size = 30
master_database_size = 6
sybsystemprocs_device_physical_name = /opt/sybase/data/sysprocs.dat
sybsystemprocs_device_size = 120
sybsystemprocs_database_size = 120
errorlog = /opt/sybase/ASE-12_5/install/VIRTUALX.log
configfile = /opt/sybase/ASE-12_5/VIRTUALX.cfg
sybsystemdb_device_physical_name = 
sybsystemdb_device_size = 5
sybsystemdb_database_size = 5
shmem = /opt/sybase/ASE-12_5
default_backup_server = VIRTUALX_BS
server_name = VIRTUALX
force_buildmaster = yes
Fri Aug 12 09:55:26 2005: (Shell command) /opt/sybase/ASE-12_5/bin/dataserver -d/opt/sybase/data/master.dat -b30M -z2k -sVIRTUALX -e/opt/sybase/ASE-12_5/install/VIRTUALX.log -T1623 -f > /tmp/sbruemuF 2>&1 
dataserver: master device size for this server: 30.0 Mb
dataserver: master database size for this server: 6.0 Mb
dataserver: model database size for this server: 2.0 Mb
00:00000:00000:2005/08/12 09:55:27.43 kernel  Adaptive Server Enterprise Express Edition (Limits: 1 Engine, 2GB Memory, 5GB Disk space).
00:00000:00000:2005/08/12 09:55:27.66 kernel  Using config area from primary master device.
00:00000:00000:2005/08/12 09:55:27.66 server  Configuration Error: Configuration file, '/opt/sybase/VIRTUALX.cfg', does not exist.
00:00000:00000:2005/08/12 09:55:27.66 kernel  Warning: A configuration file was not specified and the default file '/opt/sybase/VIRTUALX.cfg' does not exist. SQL Server creates the default file with the default configuration.
00:00000:00000:2005/08/12 09:55:27.69 kernel  Warning: Using default file '/opt/sybase/VIRTUALX.cfg' since a configuration file was not specified. Specify a configuration file name in the RUNSERVER file to avoid this message.
00:00000:00000:2005/08/12 09:55:27.71 kernel  os_create_region: can't allocate 41359360 bytes
00:00000:00000:2005/08/12 09:55:27.71 kernel  kbcreate: couldn't create kernel region.
00:00000:00000:2005/08/12 09:55:27.71 kernel  kistartup: could not create shared memory
Fri Aug 12 09:55:28 2005: Buildmaster return code: 0.
Fri Aug 12 09:55:28 2005: (Shell command) /opt/sybase/ASE-12_5/bin/dataserver -z2k -d/opt/sybase/data/master.dat -e/opt/sybase/ASE-12_5/install/VIRTUALX.log -c/opt/sybase/ASE-12_5/VIRTUALX.cfg -M/opt/sybase/ASE-12_5 -sVIRTUALX -T1623 > /dev/null 2>&1 
Fri Aug 12 09:58:38 2005: Unable to boot server 'VIRTUALX'.[/QUOTE]
 I contacted Asia Pacific Sybase via forum and this is there reply:

"It looks like ASE could not get 40MB shared memory.

The operating system shared memory default of most Linux releases is 32MB. The minimum required by Adaptive Server is 64MB for a default Server with 2K pages. You must increase the amount of shared memory if you plan to increase the total memory of Adaptive Server.

Please check the Installation guide chapter 1 "Pre-Installation Task" to verified your Linux share memory setting. "

So my question is how do I increase Ubuntu shared memory to 64MB?

Please help...

---

### Post by ktklin on 2006-05-08
Hi, 

look for the value set in /proc/sys/kernel/shmmax and increase it 
by using e.g. "echo 40000000 > /proc/sys/kernel/shmmax"

Then try to restart the installation procedure.

hth

Kurt

[QUOTE=arlie]I contacted Asia Pacific Sybase via forum and this is there reply:

"It looks like ASE could not get 40MB shared memory.

The operating system shared memory default of most Linux releases is 32MB. The minimum required by Adaptive Server is 64MB for a default Server with 2K pages. You must increase the amount of shared memory if you plan to increase the total memory of Adaptive Server.

Please check the Installation guide chapter 1 "Pre-Installation Task" to verified your Linux share memory setting. "

So my question is how do I increase Ubuntu shared memory to 64MB?

Please help...[/QUOTE]

---

