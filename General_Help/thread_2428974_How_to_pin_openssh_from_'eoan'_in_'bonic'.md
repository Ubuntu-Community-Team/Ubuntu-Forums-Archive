---
title: "How to pin openssh from 'eoan' in 'bonic'"
date: 2019-10-11
forum: General Help
---

### Post by sasatefa2009 on 2019-10-11
[COLOR=#1C1E29]Hello everyone,[/COLOR]
[COLOR=#1C1E29]
[/COLOR]
[COLOR=#1C1E29]I want to pin **only** "openssh-server" package from eoan to my current bionic distro which has an old openssh version.
[/COLOR]
[COLOR=#1C1E29]the current version of openssh in bionic is 7.6 which was released "3 October 2017" means its 2 years old and this is a disaster since oepnssh is a crucial application and must be updated as soon a new version is released.[/COLOR]
[COLOR=#1C1E29]
[/COLOR]
[COLOR=#1C1E29]the current version of openssh is 8.1 with tons of bug fixes and security improvements.[/COLOR]
[COLOR=#1C1E29]
[/COLOR]
[COLOR=#1C1E29]currently, eoan has the openssh 8.1 and i want to pin it to my distro which is bionic and to receive updates whenever there is any.[/COLOR]
[COLOR=#1C1E29]
[/COLOR]
[COLOR=#1C1E29]i was unsuccessful with the pinning attempt i tried, so, i would very much appreciate your help.[/COLOR]
[COLOR=#1C1E29]

[/COLOR]
[COLOR=#1C1E29]thanks,[/COLOR]

---

### Post by CatKiller on 2019-10-11
All security fixes are already backported to the LTS releases.

---

### Post by sasatefa2009 on 2019-10-11
> **CatKiller said:**
> All security fixes are already backported to the LTS releases.

are you referring to ubuntu security fixes or openssh ?

---

### Post by CatKiller on 2019-10-11
> **sasatefa2009 said:**
> are you referring to ubuntu security fixes or openssh ?

Yes.

Security patches are applied for all the repository packages. Canonical maintain the ones with the Ubuntu logo, the community does the others.

Breaking your package management to install a fixed version from a different release would be counterproductive.

---

### Post by TheFu on 2019-10-11
[https://launchpad.net/bugs/cve/CVE-2019-6111](https://launchpad.net/bugs/cve/CVE-2019-6111) is an example of a corrected CVE.
```
sudo apt update && sudo apt upgrade
```
does the patching, assuming you are on a currently supported release.  Most of the time, Canonical is 1 day behind at worst.  Over the years, I've only altered my normal weekend patching 2 times for some high risk servers running active attacked services.

People coming from RHEL/CentOS sometimes forget to "update", which isn't automatic on Ubuntu Servers as part of the upgrade process.

---

### Post by sasatefa2009 on 2019-10-12
Well, there are some security fixes applied but there are tons aren't applied. which are made by the openssh team.
you can read and compare the changelog here [bionic ]("http://changelogs.ubuntu.com/changelogs/pool/main/o/openssh/openssh_7.6p1-4ubuntu0.3/changelog")and [eoan]("http://changelogs.ubuntu.com/changelogs/pool/main/o/openssh/openssh_8.0p1-6build1/changelog").

I'd like to see openssh updated in all ubuntu distros as soon there is a new version with ubuntu security updates apllied as well to all distros.

take a look for example at firefox package. it updated to latest version in all distros when ever there is a new update.

openssh must be treated the same and must be considered a high priority package, something as a part of ubuntu it-self.


i currently add the eoan mirror to my [COLOR=#333333][FONT=monospace]sources.list and make **sudo apt update** and then **sudo apt install ssh**

and then comment the eoan mirror again and make **sudo apt update**.
[/FONT][/COLOR]

---

### Post by guiverc on 2019-10-12
Firefox is not a good comparison; it's packaging is maintained by Mozilla themselves, the openssh team do not package openssh for Ubuntu so your comparison is flawed in my opinion. 

Openssh is a security 'high-priority' package maintained by Canonical - and is treated as such.

 If you install `openssh-client` from eoan ([https://packages.ubuntu.com/eoan/openssh-client](https://packages.ubuntu.com/eoan/openssh-client)) you'll have to check all dependencies are also met, or they'll need upgrading too. Then you'll have to check other packages/programs on your system(s) that will be impacted by those changes etc.  Also these may change, so you'll have to monitor those into the future - so what you're asking isn't as simple as you want. You'll also find security changes will be required as you may stop receiving packages when 19.10/eoan goes EOL; thus your servers will need a lot more manual maintenance that they don't now.  I don't think you're fully appreciating the 'risk' of your 'attempted solution' and potentially much-larger-holes you're introducing on yourself that currently aren't there; which to me are worse than the 'minor' issues  already not deemed security risks thus not being back-ported - that you believe will be solved.

---

### Post by The Cog on 2019-10-12
> **sasatefa2009 said:**
> Well, there are some security fixes applied but there are tons aren't applied. which are made by the openssh team.
you can read and compare the changelog here [bionic ]("http://changelogs.ubuntu.com/changelogs/pool/main/o/openssh/openssh_7.6p1-4ubuntu0.3/changelog")and [eoan]("http://changelogs.ubuntu.com/changelogs/pool/main/o/openssh/openssh_8.0p1-6build1/changelog").


I had a quick look, and both releases have changes logged for the same two 2019 CVE vulnerabilities - CVE-2019-6111 and CVE-2019-6109. 
Two vulnerability fixes in both for 2018 - CVE-2018-15473 and CVE-2018-20685.
I admit I didn't go back to 2017, but it does look to me as though security fixes are being backported to the earlier release. As indeed Canonical claim. That's why you get security updates on released versions of Ubuntu.

---

### Post by sasatefa2009 on 2019-10-12
> **guiverc said:**
> Firefox is not a good comparison; it's packaging is maintained by Mozilla themselves, the openssh team do not package openssh for Ubuntu so your comparison is flawed in my opinion. 

Openssh is a security 'high-priority' package maintained by Canonical - and is treated as such.

If you install `openssh-client` from eoan ([https://packages.ubuntu.com/eoan/openssh-client](https://packages.ubuntu.com/eoan/openssh-client)) you'll have to check all dependencies are also met, or they'll need upgrading too. Then you'll have to check other packages/programs on your system(s) that will be impacted by those changes etc. Also these may change, so you'll have to monitor those into the future - so what you're asking isn't as simple as you want. You'll also find security changes will be required as you may stop receiving packages when 19.10/eoan goes EOL; thus your servers will need a lot more manual maintenance that they don't now. I don't think you're fully appreciating the 'risk' of your 'attempted solution' and potentially much-larger-holes you're introducing on yourself that currently aren't there; which to me are worse than the 'minor' issues already not deemed security risks thus not being back-ported - that you believe will be solved.

[B]Well, sir, you have to convince me then that these changes below are not necessary
[/B]

> **The Cog said:**
> I had a quick look, and both releases have changes logged for the same two 2019 CVE vulnerabilities - CVE-2019-6111 and CVE-2019-6109. 
Two vulnerability fixes in both for 2018 - CVE-2018-15473 and CVE-2018-20685.
I admit I didn't go back to 2017, but it does look to me as though security fixes are being backported to the earlier release. As indeed Canonical claim. That's why you get security updates on released versions of Ubuntu.

Well, i took the time to parse the changes in both and these are the changes that doesn't exist in the openssh for bionic.


```
openssh (1:8.0p1-6build1) eoan; urgency=medium

  * No-change rebuild to drop runit dependency


openssh (1:8.0p1-6) unstable; urgency=medium

  * Only run dh_runit on openssh-server (closes: #935936).


openssh (1:8.0p1-5) unstable; urgency=medium

  [ Lorenzo Puliti ]
  * Add a runscript for runit (closes: #933999).


openssh (1:8.0p1-4) unstable; urgency=medium

  * Use debhelper-compat instead of debian/compat.
  * debian/*.apport:
    - Remove #! lines.
    - Avoid star imports.
    - Fix flake8 errors.
  * Run regression tests against the Python 3 version of Twisted Conch.


openssh (1:8.0p1-3) unstable; urgency=medium

  * Upload to unstable.


openssh (1:8.0p1-2) experimental; urgency=medium

  * Fix interop tests for recent regress changes.


openssh (1:8.0p1-1) experimental; urgency=medium

  * New upstream release ([https://www.openssh.com/txt/release-8.0](https://www.openssh.com/txt/release-8.0), closes:
    #927792):
    - ssh(1), ssh-agent(1), ssh-add(1): Add support for ECDSA keys in
      PKCS#11 tokens (LP: #1665695).
    - ssh(1), sshd(8): Add experimental quantum-computing resistant key
      exchange method, based on a combination of Streamlined NTRU Prime
      4591^761 and X25519.
    - ssh-keygen(1): Increase the default RSA key size to 3072 bits,
      following NIST Special Publication 800-57's guidance for a 128-bit
      equivalent symmetric security level (LP: #1445625).
    - ssh(1): Allow "PKCS11Provider=none" to override later instances of the
      PKCS11Provider directive in ssh_config.
    - sshd(8): Add a log message for situations where a connection is
      dropped for attempting to run a command but a sshd_config
      ForceCommand=internal-sftp restriction is in effect.
    - ssh(1): When prompting whether to record a new host key, accept the
      key fingerprint as a synonym for "yes".  This allows the user to paste
      a fingerprint obtained out of band at the prompt and have the client
      do the comparison for you.
    - ssh-keygen(1): When signing multiple certificates on a single
      command-line invocation, allow automatically incrementing the
      certificate serial number.
    - scp(1), sftp(1): Accept -J option as an alias to ProxyJump on the scp
      and sftp command-lines.
    - ssh-agent(1), ssh-pkcs11-helper(8), ssh-add(1): Accept "-v"
      command-line flags to increase the verbosity of output; pass verbose
      flags though to subprocesses, such as ssh-pkcs11-helper started from
      ssh-agent.
    - ssh-add(1): Add a "-T" option to allowing testing whether keys in an
      agent are usable by performing a signature and a verification.
    - sftp-server(8): Add a "lsetstat@openssh.com" protocol extension that
      replicates the functionality of the existing SSH2_FXP_SETSTAT
      operation but does not follow symlinks.
    - sftp(1): Add "-h" flag to chown/chgrp/chmod commands to request they
      do not follow symlinks.
    - sshd(8): Expose $SSH_CONNECTION in the PAM environment.  This makes
      the connection 4-tuple available to PAM modules that wish to use it in
      decision-making.
    - sshd(8): Add a ssh_config "Match final" predicate.  Matches in same
      pass as "Match canonical" but doesn't require hostname
      canonicalisation be enabled.
    - sftp(1): Support a prefix of '@' to suppress echo of sftp batch
      commands.
    - ssh-keygen(1): When printing certificate contents using "ssh-keygen
      -Lf /path/certificate", include the algorithm that the CA used to sign
      the cert.
    - sshd(8): Fix authentication failures when sshd_config contains
      "AuthenticationMethods any" inside a Match block that overrides a more
      restrictive default.
    - sshd(8): Avoid sending duplicate keepalives when ClientAliveCount is
      enabled.
    - sshd(8): Fix two race conditions related to SIGHUP daemon restart.
      Remnant file descriptors in recently-forked child processes could
      block the parent sshd's attempt to listen(2) to the configured
      addresses.  Also, the restarting parent sshd could exit before any
      child processes that were awaiting their re-execution state had
      completed reading it, leaving them in a fallback path.
    - ssh(1): Fix stdout potentially being redirected to /dev/null when
      ProxyCommand=- was in use.
    - sshd(8): Avoid sending SIGPIPE to child processes if they attempt to
      write to stderr after their parent processes have exited.
    - ssh(1): Fix bad interaction between the ssh_config ConnectTimeout and
      ConnectionAttempts directives - connection attempts after the first
      were ignoring the requested timeout (LP: #1798049).
    - ssh-keyscan(1): Return a non-zero exit status if no keys were found
      (closes: #374980, LP: #1661745).
    - scp(1): Sanitize scp filenames to allow UTF-8 characters without
      terminal control sequences.
    - sshd(8): Fix confusion between ClientAliveInterval and time-based
      RekeyLimit that could cause connections to be incorrectly closed.
    - ssh(1), ssh-add(1): Correct some bugs in PKCS#11 token PIN handling at
      initial token login.  The attempt to read the PIN could be skipped in
      some cases, particularly on devices with integrated PIN readers.  This
      would lead to an inability to retrieve keys from these tokens.
    - ssh(1), ssh-add(1): Support keys on PKCS#11 tokens that set the
      CKA_ALWAYS_AUTHENTICATE flag by requring a fresh login after the
      C_SignInit operation.
    - ssh(1): Improve documentation for ProxyJump/-J, clarifying that local
      configuration does not apply to jump hosts.
    - ssh-keygen(1): Clarify manual - ssh-keygen -e only writes public keys,
      not private.
    - ssh(1), sshd(8): be more strict in processing protocol banners,
      allowing \r characters only immediately before \n.
    - Various: fix a number of memory leaks.
    - scp(1), sftp(1): fix calculation of initial bandwidth limits.  Account
      for bytes written before the timer starts and adjust the schedule on
      which recalculations are performed.  Avoids an initial burst of
      traffic and yields more accurate bandwidth limits.
    - sshd(8): Only consider the ext-info-c extension during the initial key
      eschange.  It shouldn't be sent in subsequent ones, but if it is
      present we should ignore it.  This prevents sshd from sending a
      SSH_MSG_EXT_INFO for REKEX for these buggy clients.
    - ssh-keygen(1): Clarify manual that ssh-keygen -F (find host in
      authorized_keys) and -R (remove host from authorized_keys) options may
      accept either a bare hostname or a [hostname]:port combo.
    - ssh(1): Don't attempt to connect to empty SSH_AUTH_SOCK.
    - sshd(8): Silence error messages when sshd fails to load some of the
      default host keys.  Failure to load an explicitly-configured hostkey
      is still an error, and failure to load any host key is still fatal.
    - ssh(1): Redirect stderr of ProxyCommands to /dev/null when ssh is
      started with ControlPersist; prevents random ProxyCommand output from
      interfering with session output.
    - ssh(1): The ssh client was keeping a redundant ssh-agent socket
      (leftover from authentication) around for the life of the connection.
    - sshd(8): Fix bug in HostbasedAcceptedKeyTypes and
      PubkeyAcceptedKeyTypes options.  If only RSA-SHA2 signature types were
      specified, then authentication would always fail for RSA keys as the
      monitor checks only the base key (not the signature algorithm) type
      against *AcceptedKeyTypes.
    - ssh(1): Request correct signature types from ssh-agent when
      certificate keys and RSA-SHA2 signatures are in use.
    - sshd(8): Don't set $MAIL if UsePAM=yes as PAM typically specifies the
      user environment if it's enabled (closes: #189920, #532754).
  * Mostly resynced GSSAPI key exchange patch with Fedora.  Major changes:
    - Support selection of GSSAPI key exchange algorithms.
    - Support GSSAPI key exchange methods with DH and SHA2.
    - Support GSSAPI key exchange using ECDH and SHA2.
    - Make sure the Kerberos tickets are cleaned up with the user context.
    - Enable gssapi-keyex authentication without gssapi-with-mic.
    - Allow querying for GSSAPI key exchange algorithms from ssh (-Q
      kex-gss).
  * Apply upstream patch to fix the utimensat regression tests when not
    using the compatibility implementation.


openssh (1:7.9p1-10) unstable; urgency=medium

  * Temporarily revert IPQoS defaults to pre-7.8 values until issues with
    "iptables -m tos" and VMware have been fixed (closes: #923879, #926229;
    LP: #1822370).


openssh (1:7.9p1-9) unstable; urgency=medium

  * Apply upstream patch to make scp handle shell-style brace expansions
    when checking that filenames sent by the server match what the client
    requested (closes: #923486).


openssh (1:7.9p1-8) unstable; urgency=medium

  [ Colin Watson ]
  * Apply upstream patch to fix bug in HostbasedAcceptedKeyTypes and
    PubkeyAcceptedKeyTypes options in the case where only RSA-SHA2 signature
    types were specified.
  * Apply upstream patch to request RSA-SHA2 signatures for
    rsa-sha2-{256|512}-cert-v01@openssh.com cert algorithms (closes:
    #923419).
  * Move moduli(5) manual page to openssh-server to go with /etc/ssh/moduli;
    forgotten in 1:7.9p1-5.

  [ Dominik George ]
  * Correctly handle conffile move to openssh-server (closes: #919344).


openssh (1:7.9p1-7) unstable; urgency=medium

  * Recommend "default-logind | logind | libpam-systemd" rather than just
    libpam-systemd (closes: #923199).  (I've retained libpam-systemd as an
    alternative for a while to avoid backporting accidents, although it can
    be removed later.)
  * Pass "--exec /usr/sbin/sshd" to start-stop-daemon on stop as well as
    start and pass "--chuid 0:0" on start, to avoid problems with non-root
    groups leaking into the ownership of /run/sshd.pid (closes: #922365).


openssh (1:7.9p1-5) unstable; urgency=high

  * Move /etc/ssh/moduli to openssh-server, since it's reasonably large and
    only used by sshd (closes: #858050).
  * Drop obsolete alternate build-dependency on libssl1.0-dev (closes:
    #917342).


openssh (1:7.9p1-4) unstable; urgency=medium

  * Fix Ubuntu detection in debian/rules, since the documentation comment
    for dpkg_vendor_derives_from is wrong (thanks, Jeremy Bicha; see
    #913816).


openssh (1:7.9p1-3) unstable; urgency=medium

  * Be more specific about what files to install in openssh-tests, to avoid
    installing a symlink into the build tree.
  * Re-export debian/upstream/signing-key.asc without extra signatures.
  * Restore direct test dependencies on openssl, putty-tools, and
    python-twisted-conch; these are really only indirect dependencies via
    openssh-tests, but including them means that this package will be
    retested when they change.


openssh (1:7.9p1-2) unstable; urgency=medium

  * Add GitLab CI configuration.
  * Make the autopkgtest create /run/sshd if it doesn't already exist.
  * Drop "set -x" verbosity from the autopkgtest; I think we can do without
    this in most cases nowadays.
  * Add an openssh-tests binary package containing enough files to run the
    upstream regression tests.  This allows autopkgtest to run more
    efficiently, as it doesn't have to build part of the source tree again.


openssh (1:7.9p1-1) unstable; urgency=medium

  * New upstream release ([https://www.openssh.com/txt/release-7.9):](https://www.openssh.com/txt/release-7.9):)
    - ssh(1), sshd(8): allow most port numbers to be specified using service
      names from getservbyname(3) (typically /etc/services; closes:
      #177406).
    - ssh(1): allow the IdentityAgent configuration directive to accept
      environment variable names.  This supports the use of multiple agent
      sockets without needing to use fixed paths.
    - sshd(8): support signalling sessions via the SSH protocol.  A limited
      subset of signals is supported and only for login or command sessions
      (i.e. not subsystems) that were not subject to a forced command via
      authorized_keys or sshd_config.
    - ssh(1): support "ssh -Q sig" to list supported signature options.
      Also "ssh -Q help" to show the full set of supported queries.
    - ssh(1), sshd(8): add a CASignatureAlgorithms option for the client and
      server configs to allow control over which signature formats are
      allowed for CAs to sign certificates.  For example, this allows
      banning CAs that sign certificates using the RSA-SHA1 signature
      algorithm.
    - sshd(8), ssh-keygen(1): allow key revocation lists (KRLs) to revoke
      keys specified by SHA256 hash.
    - ssh-keygen(1): allow creation of key revocation lists directly from
      base64-encoded SHA256 fingerprints.  This supports revoking keys using
      only the information contained in sshd(8) authentication log messages.
    - ssh(1), ssh-keygen(1): avoid spurious "invalid format" errors when
      attempting to load PEM private keys while using an incorrect
      passphrase.
    - sshd(8): when a channel closed message is received from a client,
      close the stderr file descriptor at the same time stdout is closed.
      This avoids stuck processes if they were waiting for stderr to close
      and were insensitive to stdin/out closing (closes: #844494).
    - ssh(1): allow ForwardX11Timeout=0 to disable the untrusted X11
      forwarding timeout and support X11 forwarding indefinitely.
      Previously the behaviour of ForwardX11Timeout=0 was undefined.
    - sshd(8): when compiled with GSSAPI support, cache supported method
      OIDs regardless of whether GSSAPI authentication is enabled in the
      main section of sshd_config.  This avoids sandbox violations if GSSAPI
      authentication was later enabled in a Match block.
    - sshd(8): do not fail closed when configured with a text key revocation
      list that contains a too-short key.
    - ssh(1): treat connections with ProxyJump specified the same as ones
      with a ProxyCommand set with regards to hostname canonicalisation
      (i.e. don't try to canonicalise the hostname unless
      CanonicalizeHostname is set to 'always').
    - ssh(1): fix regression in OpenSSH 7.8 that could prevent public-key
      authentication using certificates hosted in a ssh-agent(1) or against
      sshd(8) from OpenSSH <7.8 (LP: #1790963).
    - All: support building against the openssl-1.1 API (releases 1.1.0g and
      later).  The openssl-1.0 API will remain supported at least until
      OpenSSL terminates security patch support for that API version
      (closes: #828475).
    - sshd(8): allow the futex(2) syscall in the Linux seccomp sandbox;
      apparently required by some glibc/OpenSSL combinations.
  * Remove dh_builddeb override to use xz compression; this has been the
    default since dpkg 1.17.0.
  * Simplify debian/rules using /usr/share/dpkg/default.mk.
  * Remove /etc/network/if-up.d/openssh-server, as it causes more problems
    than it solves (thanks, Christian Ehrhardt, Andreas Hasenack, and David
    Britton; closes: #789532, LP: #1037738, #1674330, #1718227).  Add an
    "if-up hook removed" section to README.Debian documenting the corner
    case that may need configuration adjustments.


openssh (1:7.8p1-1) unstable; urgency=medium

  * New upstream release ([https://www.openssh.com/txt/release-7.8](https://www.openssh.com/txt/release-7.8), closes:
    #907534):
    - ssh-keygen(1): Write OpenSSH format private keys by default instead of
      using OpenSSL's PEM format (closes: #905407).  The OpenSSH format,
      supported in OpenSSH releases since 2014 and described in the
      PROTOCOL.key file in the source distribution, offers substantially
      better protection against offline password guessing and supports key
      comments in private keys.  If necessary, it is possible to write old
      PEM-style keys by adding "-m PEM" to ssh-keygen's arguments when
      generating or updating a key.
    - sshd(8): Remove internal support for S/Key multiple factor
      authentication.  S/Key may still be used via PAM or BSD auth.
    - ssh(1): Remove vestigial support for running ssh(1) as setuid.  This
      used to be required for hostbased authentication and the (long gone)
      rhosts-style authentication, but has not been necessary for a long
      time.  Attempting to execute ssh as a setuid binary, or with uid !=
      effective uid will now yield a fatal error at runtime.
    - sshd(8): The semantics of PubkeyAcceptedKeyTypes and the similar
      HostbasedAcceptedKeyTypes options have changed.  These now specify
      signature algorithms that are accepted for their respective
      authentication mechanism, where previously they specified accepted key
      types.  This distinction matters when using the RSA/SHA2 signature
      algorithms "rsa-sha2-256", "rsa-sha2-512" and their certificate
      counterparts.  Configurations that override these options but omit
      these algorithm names may cause unexpected authentication failures (no
      action is required for configurations that accept the default for
      these options).
    - sshd(8): The precedence of session environment variables has changed.
      ~/.ssh/environment and environment="..." options in authorized_keys
      files can no longer override SSH_* variables set implicitly by sshd.
    - ssh(1)/sshd(8): The default IPQoS used by ssh/sshd has changed.  They
      will now use DSCP AF21 for interactive traffic and CS1 for bulk.  For
      a detailed rationale, please see the commit message:
      [https://cvsweb.openbsd.org/src/usr.bin/ssh/readconf.c#rev1.284](https://cvsweb.openbsd.org/src/usr.bin/ssh/readconf.c#rev1.284)
    - ssh(1)/sshd(8): Add new signature algorithms "rsa-sha2-256-cert-
      [EMAIL="v01@openssh.com"]v01@openssh.com[/EMAIL]" and "rsa-sha2-512-cert-v01@openssh.com" to explicitly
      force use of RSA/SHA2 signatures in authentication.
    - sshd(8): Extend the PermitUserEnvironment option to accept a whitelist
      of environment variable names in addition to global "yes" or "no"
      settings.
    - sshd(8): Add a PermitListen directive to sshd_config(5) and a
      corresponding permitlisten= authorized_keys option that control which
      listen addresses and port numbers may be used by remote forwarding
      (ssh -R ...).
    - sshd(8): Add some countermeasures against timing attacks used for
      account validation/enumeration.  sshd will enforce a minimum time or
      each failed authentication attempt consisting of a global 5ms minimum
      plus an additional per-user 0-4ms delay derived from a host secret.
    - sshd(8): Add a SetEnv directive to allow an administrator to
      explicitly specify environment variables in sshd_config.  Variables
      set by SetEnv override the default and client-specified environment.
    - ssh(1): Add a SetEnv directive to request that the server sets an
      environment variable in the session.  Similar to the existing SendEnv
      option, these variables are set subject to server configuration.
    - ssh(1): Allow "SendEnv -PATTERN" to clear environment variables
      previously marked for sending to the server (closes: #573316).
    - ssh(1)/sshd(8): Make UID available as a %-expansion everywhere that
      the username is available currently.
    - ssh(1): Allow setting ProxyJump=none to disable ProxyJump
      functionality.
    - sshd(8): Avoid observable differences in request parsing that could be
      used to determine whether a target user is valid.
    - ssh(1)/sshd(8): Fix some memory leaks.
    - ssh(1): Fix a pwent clobber (introduced in openssh-7.7) that could
      occur during key loading, manifesting as crash on some platforms.
    - sshd_config(5): Clarify documentation for AuthenticationMethods
      option.
    - ssh(1): Ensure that the public key algorithm sent in a public key
      SSH_MSG_USERAUTH_REQUEST matches the content of the signature blob.
      Previously, these could be inconsistent when a legacy or non-OpenSSH
      ssh-agent returned a RSA/SHA1 signature when asked to make a RSA/SHA2
      signature.
    - sshd(8): Fix failures to read authorized_keys caused by faulty
      supplemental group caching.
    - scp(1): Apply umask to directories, fixing potential mkdir/chmod race
      when copying directory trees.
    - ssh-keygen(1): Return correct exit code when searching for and hashing
      known_hosts entries in a single operation.
    - ssh(1): Prefer the ssh binary pointed to via argv[0] to $PATH when
      re-executing ssh for ProxyJump.
    - sshd(8): Do not ban PTY allocation when a sshd session is restricted
      because the user password is expired as it breaks password change
      dialog.
    - ssh(1)/sshd(8): Fix error reporting from select() failures.
    - ssh(1): Improve documentation for -w (tunnel) flag, emphasising that
      -w implicitly sets Tunnel=point-to-point.
    - ssh-agent(1): Implement EMFILE mitigation for ssh-agent.  ssh-agent
      will no longer spin when its file descriptor limit is exceeded.
    - ssh(1)/sshd(8): Disable SSH2_MSG_DEBUG messages for Twisted Conch
      clients.  Twisted Conch versions that lack a version number in their
      identification strings will mishandle these messages when running on
      Python 2.x ([https://twistedmatrix.com/trac/ticket/9422](https://twistedmatrix.com/trac/ticket/9422)).
    - sftp(1): Notify user immediately when underlying ssh process dies
      expectedly.
    - ssh(1)/sshd(8): Fix tunnel forwarding; regression in 7.7 release.
    - ssh-agent(1): Don't kill ssh-agent's listening socket entirely if it
      fails to accept(2) a connection.
    - ssh(1): Add some missing options in the configuration dump output (ssh
      -G).
    - sshd(8): Expose details of completed authentication to PAM auth
      modules via SSH_AUTH_INFO_0 in the PAM environment.
  * Switch debian/watch to HTTPS.
  * Temporarily work around [https://twistedmatrix.com/trac/ticket/9515](https://twistedmatrix.com/trac/ticket/9515) in
    regression tests.


openssh (1:7.7p1-3) unstable; urgency=medium

  [ Colin Watson ]
  * Adjust git-dpm tagging configuration.
  * Remove no-longer-used Lintian overrides from openssh-server and ssh.
  * Add Documentation keys to ssh-agent.service, ssh.service, and
    ssh@.service.

  [ Juri Grabowski ]
  * Add rescue.target with ssh support.

  [ Christian Ehrhardt ]
  * Fix unintentional restriction of authorized keys environment options
    to be alphanumeric (closes: #903474, LP: #1771011).


openssh (1:7.7p1-2) unstable; urgency=medium

  * Fix parsing of DebianBanner option (closes: #894730).


openssh (1:7.7p1-1) unstable; urgency=medium

  * New upstream release ([https://www.openssh.com/txt/release-7.7):](https://www.openssh.com/txt/release-7.7):)
    - ssh(1)/sshd(8): Drop compatibility support for some very old SSH
      implementations, including ssh.com <=2.* and OpenSSH <= 3.*.  These
      versions were all released in or before 2001 and predate the final SSH
      RFCs.  The support in question isn't necessary for RFC-compliant SSH
      implementations.
    - Add experimental support for PQC XMSS keys (Extended Hash-Based
      Signatures).
    - sshd(8): Add an "rdomain" criterion for the sshd_config Match keyword
      to allow conditional configuration that depends on which routing
      domain a connection was received on.
    - sshd_config(5): Add an optional rdomain qualifier to the ListenAddress
      directive to allow listening on different routing domains.
    - sshd(8): Add "expiry-time" option for authorized_keys files to allow
      for expiring keys.
    - ssh(1): Add a BindInterface option to allow binding the outgoing
      connection to an interface's address (basically a more usable
      BindAddress; closes: #289592).
    - ssh(1): Expose device allocated for tun/tap forwarding via a new %T
      expansion for LocalCommand.  This allows LocalCommand to be used to
      prepare the interface.
    - sshd(8): Expose the device allocated for tun/tap forwarding via a new
      SSH_TUNNEL environment variable.  This allows automatic setup of the
      interface and surrounding network configuration automatically on the
      server.
    - ssh(1)/scp(1)/sftp(1): Add URI support to ssh, sftp and scp, e.g.
      ssh://user@host or sftp://user@host/path.  Additional connection
      parameters described in draft-ietf-secsh-scp-sftp-ssh-uri-04 are not
      implemented since the ssh fingerprint format in the draft uses the
      deprecated MD5 hash with no way to specify any other algorithm.
    - ssh-keygen(1): Allow certificate validity intervals that specify only
      a start or stop time (instead of both or neither).
    - sftp(1): Allow "cd" and "lcd" commands with no explicit path argument.
      lcd will change to the local user's home directory as usual.  cd will
      change to the starting directory for session (because the protocol
      offers no way to obtain the remote user's home directory).
    - sshd(8): When doing a config test with sshd -T, only require the
      attributes that are actually used in Match criteria rather than (an
      incomplete list of) all criteria.
    - ssh(1)/sshd(8): More strictly check signature types during key
      exchange against what was negotiated.  Prevents downgrade of RSA
      signatures made with SHA-256/512 to SHA-1.
    - sshd(8): Fix support for client that advertise a protocol version of
      "1.99" (indicating that they are prepared to accept both SSHv1 and
      SSHv2).  This was broken in OpenSSH 7.6 during the removal of SSHv1
      support.
    - ssh(1): Warn when the agent returns a ssh-rsa (SHA1) signature when a
      rsa-sha2-256/512 signature was requested.  This condition is possible
      when an old or non-OpenSSH agent is in use.
    - ssh-agent(1): Fix regression introduced in 7.6 that caused ssh-agent
      to fatally exit if presented an invalid signature request message.
    - sshd_config(5): Accept yes/no flag options case-insensitively, as has
      been the case in ssh_config(5) for a long time (LP: #1656557).
    - ssh(1): Improve error reporting for failures during connection.  Under
      some circumstances misleading errors were being shown.
    - ssh-keyscan(1): Add -D option to allow printing of results directly in
      SSHFP format.
    - ssh(1): Compatibility fix for some servers that erroneously drop the
      connection when the IUTF8 (RFC8160) option is sent.
    - scp(1): Disable RemoteCommand and RequestTTY in the ssh session
      started by scp (sftp was already doing this).
    - ssh-keygen(1): Refuse to create a certificate with an unusable number
      of principals.
    - ssh-keygen(1): Fatally exit if ssh-keygen is unable to write all the
      public key during key generation.  Previously it would silently ignore
      errors writing the comment and terminating newline.
    - ssh(1): Do not modify hostname arguments that are addresses by
      automatically forcing them to lower-case.  Instead canonicalise them
      jo resolve ambiguities (e.g. ::0001 => ::1) before they are matched
      against known_hosts.
    - ssh(1): Don't accept junk after "yes" or "no" responses to hostkey
      prompts.
    - sftp(1): Have sftp print a warning about shell cleanliness when
      decoding the first packet fails, which is usually caused by shells
      polluting stdout of non-interactive startups.
    - ssh(1)/sshd(8): Switch timers in packet code from using wall-clock
      time to monotonic time, allowing the packet layer to better function
      over a clock step and avoiding possible integer overflows during
      steps.
    - sshd(8): Correctly detect MIPS ABI in use at configure time.  Fixes
      sandbox violations on some environments.
    - Build and link with "retpoline" flags when available to mitigate the
      "branch target injection" style (variant 2) of the Spectre
      branch-prediction vulnerability.


openssh (1:7.6p1-5) unstable; urgency=medium

  * Explicitly build-depend on pkg-config, rather than implicitly
    build-depending on it via libgtk-3-dev (thanks, Aurelien Jarno; closes:
    #894558).

```

---

### Post by PaulW2U on 2019-10-12
> **guiverc said:**
> Firefox is not a good comparison; it's packaging is maintained by Mozilla themselves, the openssh team do not package openssh for Ubuntu so your comparison is flawed in my opinion.
Actually Chris, that's not quite correct.

The Firefox snap is provided by Mozilla but the .deb package is packaged by Canonical's Desktop Team is conjunction with the Security Team. Take a look at Firefox's 'About' screen. Thunderbird and Chromium are treated in a similar way. I'm sure that due to the sheer size of the applications, frequent new features, the number of bug fixes, and the rapid release cycle all mean that time-wise it would not be possible to backport just the security fixes to multiple releases and architectures. So in principle everyone get the latest release. (Yes, there are a few exceptions.)

For smaller packages the application of security fixes is much much less of a problem.

---

### Post by CatKiller on 2019-10-12
> **sasatefa2009 said:**
> **Well, sir, you have to convince me then that these changes below are not necessary**
They need to do no such thing.

You've come to the stunning revelation that software that's under development gets new features that would be nice to have. It's almost as if putting in new features that are nice to have is exactly what developing software means.

That doesn't mean that it's a security fix that needs to be backported, though.

If you want Eoan features, you should be using Eoan. If you want rolling release software, you should be using a rolling release distro. If you want particular new software versions to have their dependencies satisfied, you should be using a PPA.

No one here is going to say that users should be mixing-and-matching random packages from disparate releases as a matter of course. Even if *you* had a super-firm grasp of packaging and release policy, which doesn't seem all that likely given the hostility, the next random user that stumbles across the thread might not have.

You are, of course, perfectly welcome to break your package manager in whichever way you see fit; it's your system, after all. We won't be terribly inclined to help you to do so.

---

### Post by The Cog on 2019-10-12
> Well, i took the time to parse the changes in both and these are the changes that doesn't exist in the openssh for bionic.
My mistake. I thought this thread was about security updates. 

Yes, for new features, you need a newer release version, as you are trying to do. I'm afraid that porting a newer release package to an older distro release is beyond my abilities. It may be easier to compile from source, I don't know. The easiest thing would be to upgrade to Eoan after backing up the home folders.

---

### Post by SeijiSensei on 2019-10-12
The other option is building openssh from source:  [https://github.com/openssh/openssh-portable](https://github.com/openssh/openssh-portable)

---

### Post by TheFu on 2019-10-12
When running an LTS, I don't want any of the features to change.  I want things to keep working exactly as they did at install until support ends.  That usually means only back porting for security needs, never for new features.  On LTS desktops, when google, twitter, box, or some other clouding service changes something, my needs for stability and the end-user's needs for something that actually work have a conflict.  What good is a twitter application that can't actually tweet?

---

### Post by TheFu on 2019-10-12
> **The Cog said:**
> My mistake. I thought this thread was about security updates. 

Yes, for new features, you need a newer release version, as you are trying to do. I'm afraid that porting a newer release package to an older distro release is beyond my abilities. It may be easier to compile from source, I don't know. The easiest thing would be to upgrade to Eoan after backing up the home folders.

If you want new features, look for a reputable, trusted, PPA for the release you run.

---

### Post by sasatefa2009 on 2019-10-13
The changelog is not just new features, it has a lot of "**fixes**" for bugs reported by users to the openssh team.
Does the bug has to be CVE to be considered serious ?

The real question out of this hassle is, why the ubuntu team behind the openssh package are not just updating it to latest version in all distros instead of backporting certain fixes ? and who decides what a serious bug and what is not ?


The End of Standard Support for ubuntu 18.04 is April 2023, is openssh going to be at version 7.6p1 until this day with only backporting cherry-picked bugs ?

---

### Post by guiverc on 2019-10-13
> **PaulW2U said:**
> Actually Chris, that's not quite correct.

I looked and sure enough maintainer is listed as Ubuntu Core devs... My comment was based on a podcast on the weekend and what I thought I heard Popey say; and it's very expected of him to talk about snaps, but I didn't hear or register the 'snaps' as I was doing something else as I listened to it (in the hour or so before my comment).  Thanks for correction.

---

