---
title: "OpenChange  Samba4 Setup with Bind9 DNS NT_STATUS_PORT_UNREACHABLE"
date: 2013-11-26
forum: General Help
---

### Post by DantePasquale on 2013-11-26
I'm stumped on this one -- I'm using the OpenChange cookbook to install
on Ubuntu Server 12.04 64.

netstat -tapn looks weird to me, but I'm not sure what it should look
like for this configuration.

No firewall (iptables -L is empty ruleset)

I'm running the command locally.

Make and Install looks fine. When I try to create the mapiprofile for
the JohnDoe user I get the following error:

Failed to connect to remote server: ncacn_ip_tcp:192.168.4.110[]
NT_STATUS_PORT_UNREACHABLE
    MapiLogonProvider        : MAPI_E_NETWORK_ERROR (0x80040115)

Not sure what info to post to help debug this but here goes:

Command and output:

```
/usr/local/samba/bin/mapiprofile --create --profile=testing --default
--address=192.168.4.110 --domain=sfpi-test --realm=sfpi-test.local
--username=JohnDoe --password='OpenChangeDev1' --debuglevel=9
INFO: Current debug levels:
  all: 9
  tdb: 9
  printdrivers: 9
  lanman: 9
  smb: 9
  rpc_parse: 9
  rpc_srv: 9
  rpc_cli: 9
  passdb: 9
  sam: 9
  auth: 9
  winbind: 9
  vfs: 9
  idmap: 9
  quota: 9
  acls: 9
  locking: 9
  msdfs: 9
  dmapi: 9
  registry: 9
  scavenger: 9
  dns: 9
  ldb: 9
Using binding ncacn_ip_tcp:192.168.4.110
Mapped to DCERPC endpoint 135
added interface eth0 ip=192.168.4.110 bcast=192.168.7.255
netmask=255.255.252.0
added interface eth0 ip=192.168.4.110 bcast=192.168.7.255
netmask=255.255.252.0
Failed to connect to remote server: ncacn_ip_tcp:192.168.4.110[]
NT_STATUS_PORT_UNREACHABLE
    MapiLogonProvider        : MAPI_E_NETWORK_ERROR (0x80040115)
Deleting profile

```
Command for running samba:

```
PYTHONPATH=$PYTHONPATH /usr/local/samba/sbin/samba -d9 -i -M single

```
Output from samba:

```
Terminating connection - 'dcesrv: NT_STATUS_CONNECTION_DISCONNECTED'
imessaging: cleaning up /usr/local/samba/private/smbd.tmp/msg/msg.4155.75
single_terminate: reason[dcesrv: NT_STATUS_CONNECTION_DISCONNECTED]

```
Output from netstat -tapn:

```
netstat -tapn | grep 135
tcp        0      0 0.0.0.0:135             0.0.0.0:*              
LISTEN      4746/samba     
tcp        0      0 192.168.4.110:42326     192.168.4.110:135      
TIME_WAIT   -    
root@openchangedev:~# ps -ef | grep 4746
root      4746 32707  1 15:56 pts/0    00:00:00
/usr/local/samba/sbin/samba -d3 -i -M single
root      4747  4746  0 15:56 ?        00:00:00
/usr/local/samba/sbin/smbd -D --option=server role check:inhibit=yes
--foreground --log-stdout
root      4965  1505  0 15:57 pts/2    00:00:00 grep --color=auto 4746
```

Entire samba debug=3 output:

```
lpcfg_load: refreshing parameters from /usr/local/samba/etc/smb.conf
params.c:pm_process() - Processing configuration file
"/usr/local/samba/etc/smb.conf"
samba version 4.1.0 started.
Copyright Andrew Tridgell and the Samba Team 1992-2013
GENSEC backend 'gssapi_spnego' registered
GENSEC backend 'gssapi_krb5' registered
GENSEC backend 'gssapi_krb5_sasl' registered
GENSEC backend 'schannel' registered
GENSEC backend 'spnego' registered
GENSEC backend 'ntlmssp' registered
GENSEC backend 'krb5' registered
GENSEC backend 'fake_gssapi_krb5' registered
NTPTR backend 'simple_ldb'
NTVFS backend 'default' for type 1 registered
NTVFS backend 'posix' for type 1 registered
NTVFS backend 'unixuid' for type 1 registered
NTVFS backend 'unixuid' for type 3 registered
NTVFS backend 'unixuid' for type 2 registered
NTVFS backend 'cifs' for type 1 registered
NTVFS backend 'smb2' for type 1 registered
NTVFS backend 'simple' for type 1 registered
NTVFS backend 'cifsposix' for type 1 registered
NTVFS backend 'default' for type 3 registered
NTVFS backend 'default' for type 2 registered
NTVFS backend 'nbench' for type 1 registered
PROCESS_MODEL 'single' registered
PROCESS_MODEL 'standard' registered
PROCESS_MODEL 'onefork' registered
PROCESS_MODEL 'prefork' registered
AUTH backend 'sam' registered
AUTH backend 'sam_ignoredomain' registered
AUTH backend 'anonymous' registered
AUTH backend 'winbind' registered
AUTH backend 'winbind_wbclient' registered
AUTH backend 'name_to_ntstatus' registered
AUTH backend 'unix' registered
SHARE backend [classic] registered.
SHARE backend [ldb] registered.
ldb_wrap open of privilege.ldb
samba: using 'single' process model
DCERPC endpoint server 'rpcecho' registered
DCERPC endpoint server 'epmapper' registered
DCERPC endpoint server 'remote' registered
DCERPC endpoint server 'srvsvc' registered
DCERPC endpoint server 'wkssvc' registered
DCERPC endpoint server 'unixinfo' registered
DCERPC endpoint server 'samr' registered
DCERPC endpoint server 'winreg' registered
DCERPC endpoint server 'netlogon' registered
DCERPC endpoint server 'dssetup' registered
DCERPC endpoint server 'lsarpc' registered
DCERPC endpoint server 'backupkey' registered
DCERPC endpoint server 'spoolss' registered
DCERPC endpoint server 'drsuapi' registered
DCERPC endpoint server 'browser' registered
DCERPC endpoint server 'eventlog6' registered
DCERPC endpoint server 'dnsserver' registered
DCERPC endpoint server 'exchange_emsmdb' registered
DCERPC endpoint server 'exchange_nsp' registered
DCERPC endpoint server 'exchange_ds_rfr' registered
DCERPC endpoint server 'mapiproxy' registered
dreplsrv_partition[CN=Configuration,DC=sfpi-test,DC=local] loaded
dreplsrv_partition[CN=Schema,CN=Configuration,DC=sfpi-test,DC=local] loaded
dreplsrv_partition[DC=sfpi-test,DC=local] loaded
dreplsrv_partition[DC=ForestDnsZones,DC=sfpi-test,DC=local] loaded
dreplsrv_partition[DC=DomainDnsZones,DC=sfpi-test,DC=local] loaded
ldb_wrap open of secrets.ldb
ldb_wrap open of idmap.ldb
kccsrv_partition[DC=sfpi-test,DC=local] loaded
kccsrv_partition[CN=Configuration,DC=sfpi-test,DC=local] loaded
kccsrv_partition[CN=Schema,CN=Configuration,DC=sfpi-test,DC=local] loaded
kccsrv_partition[DC=DomainDnsZones,DC=sfpi-test,DC=local] loaded
kccsrv_partition[DC=ForestDnsZones,DC=sfpi-test,DC=local] loaded
Calling DNS name update script
Calling SPN name update script
/usr/local/samba/sbin/smbd: smbd version 4.1.0 started.
/usr/local/samba/sbin/smbd: Copyright Andrew Tridgell and the Samba Team
1992-2013
Child /usr/local/samba/sbin/samba_spnupdate exited with status 0 - Success
Completed SPN update check OK
Terminating connection - 'wbsrv: wbsrv_call_loop:
tstream_read_pdu_blob_recv() - NT_STATUS_CONNECTION_DISCONNECTED'
single_terminate: reason[wbsrv: wbsrv_call_loop:
tstream_read_pdu_blob_recv() - NT_STATUS_CONNECTION_DISCONNECTED]
/usr/local/samba/sbin/smbd: Unable to open printcap file /etc/printcap
for read!
Registered OPENCHANGEDEV<00> with 192.168.4.110 on interface 192.168.7.255
Registered OPENCHANGEDEV<03> with 192.168.4.110 on interface 192.168.7.255
Registered OPENCHANGEDEV<20> with 192.168.4.110 on interface 192.168.7.255
Registered SFPI-TEST<1b> with 192.168.4.110 on interface 192.168.7.255
Registered SFPI-TEST<1c> with 192.168.4.110 on interface 192.168.7.255
Registered SFPI-TEST<00> with 192.168.4.110 on interface 192.168.7.255
/usr/local/samba/sbin/samba_dnsupdate: Traceback (most recent call last):
/usr/local/samba/sbin/samba_dnsupdate:   File
"/usr/local/samba/sbin/samba_dnsupdate", line 510, in <module>
/usr/local/samba/sbin/samba_dnsupdate:     get_credentials(lp)
/usr/local/samba/sbin/samba_dnsupdate:   File
"/usr/local/samba/sbin/samba_dnsupdate", line 123, in get_credentials
/usr/local/samba/sbin/samba_dnsupdate:     raise e
/usr/local/samba/sbin/samba_dnsupdate: RuntimeError: kinit for
OPENCHANGEDEV$@SFPI-TEST.LOCAL failed (Cannot contact any KDC for
requested realm)
/usr/local/samba/sbin/samba_dnsupdate:
Child /usr/local/samba/sbin/samba_dnsupdate exited with status 1 -
Operation not permitted
../source4/dsdb/dns/dns_update.c:294: Failed DNS update -
NT_STATUS_ACCESS_DENIED
Terminating connection - 'dcesrv: NT_STATUS_CONNECTION_DISCONNECTED'
single_terminate: reason[dcesrv: NT_STATUS_CONNECTION_DISCONNECTED]
```

---

