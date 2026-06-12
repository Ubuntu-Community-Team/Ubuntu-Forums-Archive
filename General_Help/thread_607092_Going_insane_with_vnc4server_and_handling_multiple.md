---
title: "Going insane with vnc4server and handling multiple users."
date: 2007-11-08
forum: General Help
---

### Post by caban on 2007-11-08
I used xinetd to accept 5 unlisted Xvnc connections 5901-5905.

```
service Xvnc1
{
    type = UNLISTED
    disable = no
    socket_type = stream
    protocol = tcp
    wait = yes
    user = root
    server = /usr/bin/Xvnc
    server_args = -inetd :1 -query localhost -once -desktop NIX1 -DisconnectClients=0 -NeverShared -securitytypes none -extension XFIXES
    port = 5901
}

service Xvnc2
{
    type = UNLISTED
    disable = no
    socket_type = stream
    protocol = tcp
    wait = yes
    user = root
    server = /usr/bin/Xvnc
    server_args = -inetd :2 -query localhost -once -desktop NIX1 -DisconnectClients=0 -NeverShared -securitytypes none -extension XFIXES
    port = 5902
}

service Xvnc3
{
    type = UNLISTED
    disable = no
    socket_type = stream
    protocol = tcp
    wait = yes
    user = root
    server = /usr/bin/Xvnc
    server_args = -inetd :3 -query localhost -once -desktop NIX1 -DisconnectClients=0 -NeverShared -securitytypes none -extension XFIXES
    port = 5903
}

service Xvnc4
{
    type = UNLISTED
    disable = no
    socket_type = stream
    protocol = tcp
    wait = yes
    user = root
    server = /usr/bin/Xvnc
    server_args = -inetd :4 -query localhost -once -desktop NIX1 -DisconnectClients=0 -NeverShared -securitytypes none -extension XFIXES
    port = 5904
}

service Xvnc5
{
    type = UNLISTED
    disable = no
    socket_type = stream
    protocol = tcp
    wait = yes
    user = root
    server = /usr/bin/Xvnc
    server_args = -inetd :5 -query localhost -once -desktop NIX1 -DisconnectClients=0 -NeverShared -securitytypes none -extension XFIXES
    port = 5905
}
```

I then made the appropriate GDM setting changes as outlined in [http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

Everything works great!  Ports 5901 - 5905 accepting incoming connections and allow GDM logins.  However if I ever receive more than 2 simultaneous connections I get this error:

```
Nov  8 15:26:52 NIX1 xinetd[6330]: warning: can't get client address: Transport endpoint is not connected
Nov  8 15:26:52 NIX1 gdm[6114]: DEBUG: decode_packet: GIOCondition 1
Nov  8 15:26:52 NIX1 gdm[6114]: DEBUG: XDMCP: Received opcode QUERY from client ::ffff:127.0.0.1 : 32772
Nov  8 15:26:52 NIX1 gdm[6114]: DEBUG: gdm_xdmcp_host_allow: client->hostname is 127.0.0.1
Nov  8 15:26:52 NIX1 gdm[6114]: DEBUG: XDMCP: Sending WILLING to ::ffff:127.0.0.1
Nov  8 15:26:52 NIX1 gdm[6114]: DEBUG: gdm_peek_local_address_list: Could not get address from hostname!
Nov  8 15:26:52 NIX1 gdm[6114]: DEBUG: decode_packet: GIOCondition 1
Nov  8 15:26:52 NIX1 gdm[6114]: DEBUG: XDMCP: Received opcode REQUEST from client ::ffff:127.0.0.1 : 32772
Nov  8 15:26:52 NIX1 gdm[6114]: DEBUG: gdm_xdmcp_handle_request: Got REQUEST from ::ffff:127.0.0.1
Nov  8 15:26:52 NIX1 gdm[6114]: DEBUG: gdm_xdmcp_host_allow: client->hostname is 127.0.0.1
Nov  8 15:26:52 NIX1 gdm[6114]: DEBUG: gdm_xdmcp_handle_request: xdmcp_pending=0, MaxPending=4, xdmcp_sessions=2, MaxSessions=16, ManufacturerID=
Nov  8 15:26:52 NIX1 gdm[6114]: DEBUG: Maximum number of open XDMCP sessions from host \376 reached
Nov  8 15:26:52 NIX1 gdm[6114]: DEBUG: XDMCP: Sending DECLINE to ::ffff:127.0.0.1
Nov  8 15:26:52 NIX1 gdm[6114]: DEBUG: gdm_forward_query_lookup: Host ::ffff:127.0.0.1 not found

```

Most errors displayed are generic and are handled fine for the first two clients, except for:
```

Nov  8 15:26:52 NIX1 gdm[6114]: DEBUG: gdm_xdmcp_handle_request: xdmcp_pending=0, MaxPending=4, xdmcp_sessions=2, MaxSessions=16, ManufacturerID=
Nov  8 15:26:52 NIX1 gdm[6114]: DEBUG: Maximum number of open XDMCP sessions from host \376 reached
```

The problem appears to be the limitation of XDMCP_SESSIONS being set to 2.

So I set this, among other variables, to higher values in gdm.conf (then gdm.conf-custom, then factory-gdm.conf... to be sure).

```
# Maximum pending requests.
MaxPending=8
MaxPendingIndirect=8
# Maximum open XDMCP sessions at any point in time.
MaxSessions=16
# Maximum wait times.
MaxWait=15
MaxWaitIndirect=15
# How many times can a person log in from a single host.  Usually better to
# keep low to fend off DoS attacks by running many logins from a single host.
# This is now set at 2 since if the server crashes then GDM doesn't know for
# some time and wouldn't allow another session.
DisplaysPerHost=8
```

I also tried setting these higher in gdmsetup, as follows:
[IMG]http://img107.imageshack.us/img107/9579/screenshotxdmcploginwinhs7.png[/IMG]

The result, after rebooting, and setting these numbers exorbitantly high is consistent: I can never have more than 2 users logged in to VNC simultaneously.  Any help is appreciated.

---

### Post by caban on 2007-11-08
Second page and no input at all? :(

---

### Post by reckless2k2 on 2007-11-08
out of curiousity, why not just use X over ssh? is this windows to linux or linux to linux? 

X over ssh is built right in.

---

### Post by bodhi.zazen on 2007-11-08
Don't use gdm.

Just start your vnc servers and connect ;)

---

### Post by caban on 2007-11-08
> **reckless2k2 said:**
> out of curiousity, why not just use X over ssh? is this windows to linux or linux to linux? 

X over ssh is built right in.

I am going Windows to Linux with 5 users.

> **bodhi.zazen said:**
> Don't use gdm.

Just start your vnc servers and connect ;)

I have 5 users at my workplace, I would have to login as each user and start them all on each reboot.

---

### Post by bodhi.zazen on 2007-11-08
> **caban said:**
> I have 5 users at my workplace, I would have to login as each user and start them all on each reboot.

Reboot, what is that ~ LOL :twisted:

The last time I rebooted my server was with a power outage that lasted longer then battery backup (current uptime 45 days, which is short).

One rarely needs to reboot linux

If you do reboot, well that is what bash scripts are for, to automate the process.

If you vnc over ssh you can start the vnc server from the ssh connection, or add a few lines to ~/.bashrc

Check to see if the vnc server is running, and if not, start it.

Soo many options, that is what is nice 'bout Linux.

---

