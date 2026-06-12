---
title: "Need to manually update OpenSSL if possible."
date: 2014-08-17
forum: General Help
---

### Post by project722 on 2014-08-17
I'm running Ubuntu 14.04 TLS. If apt-get tells you that you are on the latest version of a package but you know there is a more updated version available is there a way to install it manually and merge the changes into the package manager and existing libraries to keep things from breaking? Or if it is possible to install outside of a package manager would it be better to have a separate install and just run it out of a new folder? For example apt-get tells me I am on the latest version of OpenSSL (1.0.1f) but I would like to install 1.0.1h.

---

### Post by nerdtron on 2014-08-17
May I ask why you want the 1.0.1h version? This isn't because of the heartbleed bug isn't it?

---

### Post by project722 on 2014-08-17
No I am trying to mitigate these:
1. CVE-2014-0224   
2. CVE-2014-0221 
3. CVE-2014-0195 
4. CVE-2014-0198 
5. CVE-2010-5298 &#8211; 
6. CVE-2014-3470 - 
7. CVE-2014-0076 -

---

### Post by mc4man on 2014-08-17
All of those & more have already been patched in to 14.04. 
> 
openssl (1.0.1f-1ubuntu2.5) trusty-security; urgency=medium

  * SECURITY UPDATE: double free when processing DTLS packets
    - debian/patches/CVE-2014-3505.patch: fix double free in ssl/d1_both.c.
    - CVE-2014-3505
  * SECURITY UPDATE: DTLS memory exhaustion
    - debian/patches/CVE-2014-3506.patch: fix DTLS handshake message size
      checks in ssl/d1_both.c.
    - CVE-2014-3506
  * SECURITY UPDATE: DTLS memory leak from zero-length fragments
    - debian/patches/CVE-2014-3507.patch: fix memory leak and return codes
      in ssl/d1_both.c.
    - CVE-2014-3507
  * SECURITY UPDATE: information leak in pretty printing functions
    - debian/patches/CVE-2014-3508.patch: fix OID handling in
      crypto/asn1/a_object.c, crypto/objects/obj_dat.c.
    - CVE-2014-3508
  * SECURITY UPDATE: race condition in ssl_parse_serverhello_tlsext
    - debian/patches/CVE-2014-3509.patch: fix race in ssl/t1_lib.c.
    - CVE-2014-3509
  * SECURITY UPDATE: DTLS anonymous EC(DH) denial of service
    - debian/patches/CVE-2014-3510.patch: check for server certs in
      ssl/d1_clnt.c, ssl/s3_clnt.c.
    - CVE-2014-3510
  * SECURITY UPDATE: TLS protocol downgrade attack
    - debian/patches/CVE-2014-3511.patch: properly handle fragments in
      ssl/s23_srvr.c.
    - CVE-2014-3511
  * SECURITY UPDATE: SRP buffer overrun
    - debian/patches/CVE-2014-3512.patch: check parameters in
      crypto/srp/srp_lib.c.
    - CVE-2014-3512
  * SECURITY UPDATE: crash with SRP ciphersuite in Server Hello message
    - debian/patches/CVE-2014-5139.patch: fix SRP authentication and make
      sure ciphersuite is set up correctly in ssl/s3_clnt.c, ssl/ssl_lib.c,
      ssl/s3_lib.c, ssl/ssl.h, ssl/ssl_ciph.c, ssl/ssl_locl.h.
    - CVE-2014-5139

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Thu, 07 Aug 2014 08:03:21 -0400

openssl (1.0.1f-1ubuntu2.4) trusty-security; urgency=medium

  * SECURITY UPDATE: regression with certain renegotiations (LP: #1332643)
    - debian/patches/CVE-2014-0224-regression2.patch: accept CCS after
      sending finished ssl/s3_clnt.c.

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Fri, 20 Jun 2014 13:55:11 -0400

openssl (1.0.1f-1ubuntu2.3) trusty-security; urgency=medium

  * SECURITY UPDATE: regression with tls_session_secret_cb (LP: #1329297)
    - debian/patches/CVE-2014-0224.patch: set the CCS_OK flag when using
      tls_session_secret_cb for session resumption in ssl/s3_clnt.c.

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Thu, 12 Jun 2014 08:29:16 -0400

openssl (1.0.1f-1ubuntu2.2) trusty-security; urgency=medium

  * SECURITY UPDATE: arbitrary code execution via DTLS invalid fragment
    - debian/patches/CVE-2014-0195.patch: add consistency check for DTLS
      fragments in ssl/d1_both.c.
    - CVE-2014-0195
  * SECURITY UPDATE: denial of service via DTLS recursion flaw
    - debian/patches/CVE-2014-0221.patch: handle DTLS hello request without
      recursion in ssl/d1_both.c.
    - CVE-2014-0221
  * SECURITY UPDATE: MITM via change cipher spec
    - debian/patches/CVE-2014-0224-1.patch: only accept change cipher spec
      when it is expected in ssl/s3_clnt.c, ssl/s3_pkt.c, ssl/s3_srvr.c,
      ssl/ssl3.h.
    - debian/patches/CVE-2014-0224-2.patch: don't accept zero length master
      secrets in ssl/s3_pkt.c.
    - debian/patches/CVE-2014-0224-3.patch: allow CCS after resumption in
      ssl/s3_clnt.c.
    - CVE-2014-0224
  * SECURITY UPDATE: denial of service via ECDH null session cert
    - debian/patches/CVE-2014-3470.patch: check session_cert is not NULL
      before dereferencing it in ssl/s3_clnt.c.
    - CVE-2014-3470

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Mon, 02 Jun 2014 13:57:34 -0400

openssl (1.0.1f-1ubuntu2.1) trusty-security; urgency=medium

  * SECURITY UPDATE: denial of service via use after free
    - debian/patches/CVE-2010-5298.patch: check s->s3->rbuf.left before
      releasing buffers in ssl/s3_pkt.c.
    - CVE-2010-5298
  * SECURITY UPDATE: denial of service via null pointer dereference
    - debian/patches/CVE-2014-0198.patch: if buffer was released, get a new
      one in ssl/s3_pkt.c.
    - CVE-2014-0198

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Fri, 02 May 2014 15:23:01 -0400

openssl (1.0.1f-1ubuntu2) trusty; urgency=medium

  * SECURITY UPDATE: side-channel attack on Montgomery ladder implementation
    - debian/patches/CVE-2014-0076.patch: add and use constant time swap in
      crypto/bn/bn.h, crypto/bn/bn_lib.c, crypto/ec/ec2_mult.c,
      util/libeay.num.
    - CVE-2014-0076
  * SECURITY UPDATE: memory disclosure in TLS heartbeat extension
    - debian/patches/CVE-2014-0160.patch: use correct lengths in
      ssl/d1_both.c, ssl/t1_lib.c.
    - CVE-2014-0160

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Mon, 07 Apr 2014 15:37:53 -0400

---

### Post by grahammechanical on 2014-08-17
I am not speaking from experience or as an expert but I think that with this kind of software you will need to get the code and compile it.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Another point. open ssl 1.0.1i is the latest patched version.

[http://www.openssl.org/source/](http://www.openssl.org/source/)

The Ubuntu security are not sleeping.

Regards.

---

### Post by project722 on 2014-08-18
Thanks to both of you. I have confirmed the changelog on my system and it checks out.

---

