---
title: "Unable to ssh to my Ubuntu server for past 2 days"
date: 2014-06-20
forum: General Help
---

### Post by matthew-goeres-p on 2014-06-20
SecureCRT - Version 6.1.3 (build 423)
[LOCAL] : SSH2Core version 6.1.0.423 
[LOCAL] : Connecting to XXX.XXX.XXX.XXX:22 ... 
[LOCAL] : Changing state from STATE_NOT_CONNECTED to STATE_EXPECT_KEX_INIT 
[LOCAL] : Using protocol SSH2 
[LOCAL] : RECV : Remote Identifier = "SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1" 
[LOCAL] : CAP  : Remote can re-key 
[LOCAL] : CAP  : Remote sends language in password change requests 
[LOCAL] : CAP  : Remote sends algorithm name in PK_OK packets 
[LOCAL] : CAP  : Remote sends algorithm name in public key packets 
[LOCAL] : CAP  : Remote sends algorithm name in signatures 
[LOCAL] : CAP  : Remote sends error text in open failure packets 
[LOCAL] : CAP  : Remote sends name in service accept packets 
[LOCAL] : CAP  : Remote includes port number in x11 open packets 
[LOCAL] : CAP  : Remote uses 160 bit keys for SHA1 MAC 
[LOCAL] : CAP  : Remote supports new diffie-hellman group exchange messages 
[LOCAL] : CAP  : Remote correctly handles unknown SFTP extensions 
[LOCAL] : CAP  : Remote correctly encodes OID for gssapi 
[LOCAL] : CAP  : Remote correctly uses connected addresses in forwarded-tcpip requests 
[LOCAL] : CAP  : Remote can do SFTP version 4 
[LOCAL] : CAP  : Remote x.509v3 uses ASN.1 encoding for DSA signatures 
[LOCAL] : GSS  : Requesting full delegation 
[LOCAL] : GSS : [Kerberos] SPN : [email]host@XXX.XXX.XXX.XXX[/email] 
[LOCAL] : GSS : [Kerberos] Disabling gss mechanism 
[LOCAL] : GSS : [Kerberos] InitializeSecurityContext() failed. 
[LOCAL] : GSS : [Kerberos] The specified target is unknown or unreachable  
[LOCAL] : The following key exchange method has been filtered from the key exchange method list because it is not supported: gss-group1-sha1-toWM5Slw5Ew8Mqkay+al2g==  
[LOCAL] : GSS  : Requesting full delegation 
[LOCAL] : GSS : [Kerberos w/ Group Exchange] SPN : [email]host@XXX.XXX.XXX.XXX[/email] 
[LOCAL] : GSS : [Kerberos w/ Group Exchange] Disabling gss mechanism 
[LOCAL] : GSS : [Kerberos w/ Group Exchange] InitializeSecurityContext() failed. 
[LOCAL] : GSS : [Kerberos w/ Group Exchange] The specified target is unknown or unreachable  
[LOCAL] : The following key exchange method has been filtered from the key exchange method list because it is not supported: gss-gex-sha1-toWM5Slw5Ew8Mqkay+al2g==  
[LOCAL] : SEND : KEXINIT 
[LOCAL] : RECV : Read kexinit 
[LOCAL] : Available Remote Kex Methods = diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1 
[LOCAL] : Selected Kex Method = diffie-hellman-group-exchange-sha1 
[LOCAL] : Available Remote Host Key Algos = ssh-rsa,ssh-dss 
[LOCAL] : Selected Host Key Algo = ssh-dss 
[LOCAL] : Available Remote Send Ciphers = aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr 
[LOCAL] : Selected Send Cipher = aes256-ctr 
[LOCAL] : Available Remote Recv Ciphers = aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr 
[LOCAL] : Selected Recv Cipher = aes256-ctr 
[LOCAL] : Available Remote Send Macs = hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 
[LOCAL] : Selected Send Mac = hmac-sha1 
[LOCAL] : Available Remote Recv Macs = hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 
[LOCAL] : Selected Recv Mac = hmac-sha1 
[LOCAL] : Available Remote Compressors = none,zlib@openssh.com 
[LOCAL] : Selected Compressor = none 
[LOCAL] : Available Remote Decompressors = none,zlib@openssh.com 
[LOCAL] : Selected Decompressor = none 
[LOCAL] : Changing state from STATE_EXPECT_KEX_INIT to STATE_KEY_EXCHANGE 
[LOCAL] : SEND : KEXDH_GEX_REQUEST 
[LOCAL] : RECV : KEXDH_GEX_GROUP 
[LOCAL] : SEND : KEXDH_INIT 
[LOCAL] : RECV : KEXDH_REPLY 
[LOCAL] : SEND : NEWKEYS 
[LOCAL] : Changing state from STATE_KEY_EXCHANGE to STATE_EXPECT_NEWKEYS 
[LOCAL] : RECV : NEWKEYS 
[LOCAL] : Changing state from STATE_EXPECT_NEWKEYS to STATE_CONNECTION 
[LOCAL] : SEND: SERVICE_REQUEST[ssh-userauth] 
[LOCAL] : RECV: SERVICE_ACCEPT[ssh-userauth] -- OK 
[LOCAL] : SENT : USERAUTH_REQUEST [none] 
[LOCAL] : RECV: TCP/IP close 
[LOCAL] : Changing state from STATE_CONNECTION to STATE_CLOSED 
[LOCAL] : Connected for 12 seconds, 1039 bytes sent, 1938 bytes received

---

### Post by rahulkumarc on 2014-06-21
If you have access to your Ubuntu server via remote console, you should try to login and check the logs first. That's what I would do.

---

