---
title: "Quirky question about cron"
date: 2006-08-22
forum: General Help
---

### Post by link on 2006-08-22
Hi guys,

I've got a question about cron.

So I'm running a mirror here, via debmirror in a shell script, of the Ubuntu tree. When I run the script by hand, it works fine, and mirrors the server perfectly.
```
Get Release files.
[0%] Getting: dists/dapper/Release... ok
[0%] Getting: dists/dapper/Release.gpg... ok
[0%] Getting: dists/dapper-security/Release... ok
[0%] Getting: dists/dapper-security/Release.gpg... ok
[0%] Getting: dists/dapper-updates/Release... ok
[0%] Getting: dists/dapper-updates/Release.gpg... ok
```
However, when I put a script in /etc/cron.daily that simply runs the script in question, it fails to run correctly, instead timing out.
```
Get Release files.
[0%] Getting: dists/dapper/Release... dists/dapper/Release failed md5sum check, removing
[0%] Getting: dists/dapper/Release.gpg... dists/dapper/Release.gpg failed md5sum check, removing
Release signature does not verify, use -v to see the gpg error.
[0%] Getting: dists/dapper-security/Release... dists/dapper-security/Release failed md5sum check, removing
[0%] Getting: dists/dapper-security/Release.gpg... dists/dapper-security/Release.gpg failed md5sum check, removing
Release signature does not verify, use -v to see the gpg error.
[0%] Getting: dists/dapper-updates/Release... dists/dapper-updates/Release failed md5sum check, removing
[0%] Getting: dists/dapper-updates/Release.gpg... dists/dapper-updates/Release.gpg failed md5sum check, removing
```
This perplexes me, as I am fairly sure that cron.daily runs as root. My only guess is that cron is run as root, and then is dropped down lower priviledges before running the scripts.
Has anyone seen anything like this before?

---

### Post by DoctorMO on 2006-08-22
crons don't have access to a bash enviroment, so if your script uses enviromental variables at all they will fail. all programs must be specified in full.

---

### Post by link on 2006-08-23
Right, but if the script is a bash script, with entirely internal variables, it shouldn't be an issue. Does cron have access to the running user's environment at all? This script relys on accessing the root user's GnuPG chain for verifying the Release.gpg files. I supposed I ought to go about finding a way to import the key into a temporary keychain each time the script runs.
```
#!/bin/bash
#
# Based off https://wiki.ubuntu.com/KarlGoetz/DebmirrorHowto

### Email settings ###
NOMAIL=""
MAILTO="link@localhost"

### GPG settings ###
KEY="437D05B5"
KEYRING="/usr/share/keyrings/ubuntu-archive-keyring.gpg"

### Mirror config settings ###
ARCH=i386
SECTION=main,restricted
DIST=dapper,dapper-security,dapper-updates
SERVER=us.archive.ubuntu.com
ROOT=/ubuntu
PROTOCOL=http
LOGROOT=/var/log/ubuntu-mirror
MROOT=/var/ubuntu-mirror
MIRROR=${MROOT}/ubuntu
ARGS="--nosource --progress"

### Execution ###
if [ ! -z "$1" ]; then
        if [ "$1" == "--nomail" ]; then
                NOMAIL="true"
        fi
fi
if [ -f "${KEYRING}" ]; then
        gpg --list-keys | grep ${KEY}
        if [ "$?" != "0" ]; then
                echo "Ubuntu Archive GPG Key not found. Importing..."
                gpg --keyring ${KEYRING} --export "${KEY}" | gpg --import
        fi
fi

debmirror       -a ${ARCH} \
                -s ${SECTION} \
                -h ${SERVER} \
                -d ${DIST} \
                -r ${ROOT} \
                -e ${PROTOCOL} \
                ${ARGS} \
                ${MIRROR} | tee ${LOGROOT}/mirror-`date +%Y%m%d`.log

if [ -z "$NOMAIL" ]; then
        cat ${LOGROOT}/mirror-`date +%Y%m%d`.log | mail -s "Ubuntu mirror update: `date +\"%B %d, %Y\"`" ${MAILTO}
fi
```

---

