---
title: "GnuPG Send Key Fail"
date: 2018-04-01
forum: General Help
---

### Post by kf6sgy on 2018-04-01
I have been tearing my hair out the last couple of days trying to figure out this issue and I cannot find anyone else that has the same issue.

My GPG key recently expired so I renewed it and went to send the key to the servers like I've done 3 or 4 times and I keep getting the following error:
```
gpg: sending key <fingerprint> to hkps://hkps.pool.sks-keyservers.net
gpg: keyserver send failed: Invalid argument
gpg: keyserver send failed: Invalid argument
```

I have looked through the man page and haven't seen anything that will list what arguement it is that is invalid, I also moved my gpg.conf file to see what would happen and it failed the same way.

I'm using this command to send:
```
gpg --keyserver hkps://hkps.pool.sks-keyservers.net --send-key <fingerprint>
```

Here is my ~/.gnupg/gpg.conf:
```
#
# This is an implementation of the Riseup OpenPGP Best Practices
# https://help.riseup.net/en/security/message-security/openpgp/best-practices
#


#-----------------------------
# default key
#-----------------------------

# The default key to sign with. If this option is not used, the default key is
# the first key found in the secret keyring

default-key <fingerprint>


#-----------------------------
# behavior
#-----------------------------

# Disable inclusion of the version string in ASCII armored output
no-emit-version

# Disable comment string in clear text signatures and ASCII armored messages
no-comments

# Display long key IDs
keyid-format 0xlong

# List all keys (or the specified ones) along with their fingerprints
with-fingerprint

# Display the calculated validity of user IDs during key listings
list-options show-uid-validity
verify-options show-uid-validity

# Try to use the GnuPG-Agent. With this option, GnuPG first tries to connect to
# the agent before it asks for a passphrase.
#use-agent


#-----------------------------
# keyserver
#-----------------------------

# This is the server that --recv-keys, --send-keys, and --search-keys will
# communicate with to receive keys from, send keys to, and search for keys on
#keyserver hkps://hkps.pool.sks-keyservers.net
keyserver hkps://pool.sks-keyservers.net

# Set the proxy to use for HTTP and HKP keyservers - default to the standard
# local Tor socks proxy
# It is encouraged to use Tor for improved anonymity. Preferrably use either a
# dedicated SOCKSPort for GnuPG and/or enable IsolateDestPort and
# IsolateDestAddr
#keyserver-options http-proxy=socks5-hostname://127.0.0.1:9050

# When using --refresh-keys, if the key in question has a preferred keyserver
# URL, then disable use of that preferred keyserver to refresh the key from
keyserver-options no-honor-keyserver-url

# When searching for a key with --search-keys, include keys that are marked on
# the keyserver as revoked
keyserver-options include-revoked


#-----------------------------
# algorithm and ciphers
#-----------------------------

# list of personal digest preferences. When multiple digests are supported by
# all recipients, choose the strongest one
personal-cipher-preferences AES256 AES192 AES CAST5

# list of personal digest preferences. When multiple ciphers are supported by
# all recipients, choose the strongest one
personal-digest-preferences SHA512 SHA384 SHA256 SHA224

# message digest algorithm used when signing a key
cert-digest-algo SHA512

# This preference list is used for new keys and becomes the default for
# "setpref" in the edit menu
default-preference-list SHA512 SHA384 SHA256 SHA224 AES256 AES192 AES CAST5 ZLIB BZIP2 ZIP Uncompressed
```

---

### Post by deadflowr on 2018-04-01
Shouldn't --send-key be pluralized like --send-keys?

---

### Post by kf6sgy on 2018-04-01
I went back and checked, I've tried both, each failing to send the key.

---

### Post by #&amp;thj^% on 2018-04-01
try changing  **"hkps"** to **"hkp"**

---

### Post by kf6sgy on 2018-04-01
> **1fallen said:**
> try changing  **"hkps"** to **"hkp"**

I just tried 
```
gpg --keyserver hkp://hkp.pool.sks-keyservers.net --send-key <fingerprint>
gpg --keyserver hkps://hkp.pool.sks-keyservers.net --send-key <fingerprint>
gpg --keyserver hkp://hkps.pool.sks-keyservers.net --send-key <fingerprint>
gpg --keyserver hkp.pool.sks-keyservers.net --send-key <fingerprint>
```
which all returned ```
gpg: keyserver send failed: No keyserver available
```


```
gpg --keyserver hkps.pool.sks-keyservers.net --send-key <fingerprint>
```
returns ```
gpg: keyserver send failed: Invalid argument
```

---

### Post by #&amp;thj^% on 2018-04-02
Sadly Keyserver issues are unfortunately very common, and one person reported that a proxy was his salvation:[https://github.com/tianon/gosu/issues/39](https://github.com/tianon/gosu/issues/39)

Maybe: [https://dev.gnupg.org/T2348](https://dev.gnupg.org/T2348)
This sure seems to be a very annoying problem for many. :(

---

### Post by kf6sgy on 2018-04-02
> **1fallen said:**
> Sadly Keyserver issues are unfortunately very common, and one person reported that a proxy was his salvation:[https://github.com/tianon/gosu/issues/39](https://github.com/tianon/gosu/issues/39)

Maybe: [https://dev.gnupg.org/T2348](https://dev.gnupg.org/T2348)
This sure seems to be a very annoying problem for many. :(

If my only solution is a proxy, I guess I don't need to put my public key up on the servers. Oh well, thanks for the help.

---

