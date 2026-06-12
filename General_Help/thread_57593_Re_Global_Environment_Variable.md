---
title: "Re: Global Environment Variable"
date: 2005-08-17
forum: General Help
---

### Post by arlie on 2005-08-17
I need to set environment variables globally and nothing has worked so far. Need a simple way to do this. Please help.

I'm trying to make Sybase ASE Server Express Edition run on Ubuntu. Only Red Hat, Red Flag, Turbo Linux and SUSE are officialy recognized by Sybase to be capable of running Sybase SQL Server and I would like to include Ubuntu on that list. If I'm successful with this, Ubuntu would be our official linux server for Sybase here in Cebu City, Philippines. Our company is a business software developer and distributor of Sybase SQL Server.

This is my first time to try linux and I'm trying to convince top manangement that linux is the wave of the future.

We have a large client base that we can migrate to linux.

---

### Post by heimo on 2005-08-17
[QUOTE=arlie]I need to set environment variables globally and nothing has worked so far.
[/QUOTE]

What have you tried? Have you tried to edit /etc/bash.bashrc and add lines with export VARNAME="new value"?

---

### Post by rmrf on 2005-08-17
if your talking about globally adding sections to $PATH, then /etc/profile is the place to do it.

maybe I'm not understanding fully.

---

### Post by arlie on 2005-08-20
[QUOTE=rmrf]if your talking about globally adding sections to $PATH, then /etc/profile is the place to do it.

maybe I'm not understanding fully.[/QUOTE]

The following environment variables has to be available to all users for Sybase SQL Server to run:

#
# Sybase Product Environment variables
#
SYBASE="/opt/sybase"
export SYBASE
SYBASE_OCS="OCS-12_5"
export SYBASE_OCS
PATH="/opt/sybase/OCS-12_5/bin":$PATH
export PATH
LD_LIBRARY_PATH="/opt/sybase/OCS-12_5/lib:/opt/sybase/OCS-12_5/lib3p":$LD_LIBRARY_PATH
export LD_LIBRARY_PATH
INCLUDE="/opt/sybase/OCS-12_5/include":$INCLUDE
export INCLUDE
LIB="/opt/sybase/OCS-12_5/lib":$LIB
export LIB
SYBASE_JRE="/opt/sybase/shared-1_0/JRE-1_3"
export SYBASE_JRE
PATH="/opt/sybase/JS-12_5/bin":$PATH
export PATH
SYBASE_SYSAM="SYSAM-1_0"
export SYBASE_SYSAM
LM_LICENSE_FILE="/opt/sybase/SYSAM-1_0/licenses/license.dat"
export LM_LICENSE_FILE
SYBASE_ASE="ASE-12_5"
export SYBASE_ASE
PATH="/opt/sybase/ASE-12_5/bin:/opt/sybase/ASE-12_5/install":$PATH
export PATH
LD_LIBRARY_PATH="/opt/sybase/ASE-12_5/lib":$LD_LIBRARY_PATH
export LD_LIBRARY_PATH
PATH="/opt/sybase/RPL-12_5/bin":$PATH
export PATH

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

So, where do I put this?

Thanks

---

