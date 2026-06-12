---
title: "Almost everything related to SSL broken after make install of openssl"
date: 2022-08-25
forum: General Help
---

### Post by xeon826 on 2022-08-25
I was attempting to set up a Cisco VPN and had run into some issues, in the process of trying to correct those issues I made some changes to my certificates directory and ran several commands pertaining to setting up / modifying ssl certificates on my machine, it was a few months ago so I can't remember exactly what I ran but I know a few things I did were that I built openssl from source and installed it that way, I softlinked a few folders and moved some certificates from one folder to another. I can still access sites with https but there are just a few things that don't work with ssl anymore some examples are:
[LIST]
[*]wget now returns the following:
[/LIST]
```
--2022-08-25 22:46:09--  https://ubuntuforums.org/Resolving ubuntuforums.org (ubuntuforums.org)... 185.125.188.16, 185.125.188.17
Connecting to ubuntuforums.org (ubuntuforums.org)|185.125.188.16|:443... connected.
ERROR: cannot verify ubuntuforums.org's certificate, issued by ‘CN=R3,O=Let's Encrypt,C=US’:
  Unable to locally verify the issuer's authority.
To connect to ubuntuforums.org insecurely, use `--no-check-certificate'.
```
[LIST]
[*]When I use gyazo, it now returns an error:
[/LIST]
```
Traceback (most recent call last):	5: from /usr/bin/gyazo:116:in `<main>'
	4: from /usr/lib/ruby/2.7.0/net/http.rb:932:in `start'
	3: from /usr/lib/ruby/2.7.0/net/http.rb:943:in `do_start'
	2: from /usr/lib/ruby/2.7.0/net/http.rb:1009:in `connect'
	1: from /usr/lib/ruby/2.7.0/net/protocol.rb:44:in `ssl_socket_connect'
/usr/lib/ruby/2.7.0/net/protocol.rb:44:in `connect_nonblock': SSL_connect returned=1 errno=0 state=error: certificate verify failed (unable to get local issuer certificate) (OpenSSL::SSL::SSLError)

```
[LIST]
[*]And a project I'm working on that has separate servers for the UI and API now has stopped communicating between the two, citing an openssl error "UntrustedRoot"
[/LIST]
I tried: 
[LIST]
[*]Reinstalling ca-certificates ```
[COLOR=var(--black-800)][FONT=var(--ff-mono)]sudo apt-get install --reinstall ca-certificates[/FONT][/COLOR]
```
[*]I tried ```
sudo dpkg --purge --force-depends ca-certificates
``` followed by ```
sudo apt-get -f install
``` and then ```
sudo update-ca-certificates
```
[*]I tried changing the default version of my openssl
[/LIST]
I'd like to figure out a way to revert this all back to default without having to reinstall my operating system as I have a lot of configuration on here that I'd have to enter again.

---

### Post by TheFu on 2022-08-26
Restore from the backups you made before heading down this path.  If you don't have backups, it is well passed time for a reinstall.  Under the next installation, perhaps you'll ensure that backups are made?

Linux Mint has a fresh-install wizard that will enable timeshift for backups if you choose either btrfs or ext4 for the OS file system.  If you have multiple disks/SSDs, choose ext4, as there are some nasty failure modes with mutli-disk btrfs installs.  Also, if you run virtual machines, best to avoid btrfs. There are caveats for use, but the easier answer is to avoid it.  Anyway, Mint will lead you through about 10 things post-install to make for a safer, happier, setup.  Plus, Mint doesn't add confusing snap packages.

You'll definitely want to research if the Cisco VPN version you want to run will work under Mint before going that direction.  Mint is a child distro from Ubuntu, so many things are the same. Nothing new to learn.

However, btrfs does make for better backups with timeshift. It will use the btrfs volume manager snapshot to freeze blocks of storage so clean backups are possible.  LVM can do this too.  So can ZFS, but ZFS brings other complexities and often terrible performance.  The few times I tried to use ZFS for the OS, the performance was abysmal to the point that I wiped the install and started over with LVM+ext4.

---

