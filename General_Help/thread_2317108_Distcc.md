---
title: "Distcc"
date: 2016-03-13
forum: General Help
---

### Post by Roger_H_Newell on 2016-03-13
I dunno if this is too off topic but here goes.

I'm trying to get distcc working between two machines CLIENT and SERVER I "think" I have it setup right but I am still getting this error

(dcc_build_somewhere) Warning: failed to distribute, running locally instead

NOTHING is being compiled on the server.

My configuration is as follows
CLIENT = 192.168.0.14 
SERVER = 192.168.0.15

/etc/default/distcc on SERVER
 STARTDISTCC="true"
 ALLOWEDNETS="192.168.0.0/24" 
 LISTENER="192.168.0.15"
 NICE="10"
 JOBS="16"
 ZEROCONF="false"

client 
DISTCC_HOSTS="192.168.0.15"
/etc/distcc/host set to 192.168.0.15
$HOME/.distcc/host set to 192.168.0.15

make -jx CC=distcc

I have tried on different software repos to see if there was some problem with an individual repo but the problem persists no matter the package.


The failed to distribute error is the client side error. I noticed that the server is producing the following error
distccd[1046] (dcc_job_summary) client: 192.168.0.14:40732 COMPILE_ERROR exit:1 sig:0 core:0 ret:0 time:94ms gcc certs/system_keyring.c

---

