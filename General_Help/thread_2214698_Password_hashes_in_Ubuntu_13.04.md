---
title: "Password hashes in Ubuntu 13.04"
date: 2014-04-02
forum: General Help
---

### Post by chirag5 on 2014-04-02
Where and how are password hashes stored in Ubuntu 13.04?

---

### Post by Dave_L on 2014-04-02
See:
[http://manpages.ubuntu.com/manpages/quantal/en/man5/passwd.5.html](http://manpages.ubuntu.com/manpages/quantal/en/man5/passwd.5.html)
[http://manpages.ubuntu.com/manpages/quantal/en/man5/shadow.5.html](http://manpages.ubuntu.com/manpages/quantal/en/man5/shadow.5.html)

---

### Post by papibe on 2014-04-02
Hi chirag5.

Both Ubuntu 12.04 LTS and 13.04 use a custom crypt version based on SHA-512 (read [here]("https://wiki.ubuntu.com/Security/Features")).

Here's how to find out.

Open a terminal and run this command:
```
sudo grep youruser /etc/shadow
```
(replace 'youruser' with your actual username)

DO NOT POST YOUR RESULT.

The output would look something like:
```
youruser:**$6**$8x.....
```
The 2 characters (bolded in the example) describes the method.

Then read this man:
```
man crypt
```
Go further below and you'll see a table describing which based algorithm is used:
```
              ID  | Method
              &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
              1   | MD5
              2a  | Blowfish (not in mainline glibc; added in some
                  | Linux distributions)
              5   | SHA-256 (since glibc 2.7)
              **6   | SHA-512 (since glibc 2.7)**

```
In this example, you can confirm that SHA-512 is being used as based algorithm (which is custom changed to make harder to brute forced).

I hope it helps. Let us know how it goes.
Regards.

---

