---
title: "Live Patch Error"
date: 2017-01-10
forum: General Help
---

### Post by MAC59 on 2017-01-10
Hello Everyone,

      I am not sure if this is the correct place to ask this but I didn't see any where that would be appropriate. I signed up for the live patch service, I have 3 servers that are Ubuntu Server 16.04 and I got an email for live patch so I signed up for it. My Problem is that I ran the commands exactly as instructed and got the following error

snap install canonical-livepatch

canonical-livepatch enable TOKEN

Here is the error:

canonical-livepatch enable TOKEN
2017/01/10 08:04:13 Error executing enable?auth-token=TOKEN
Connection to the daemon failed: Put [http://127.0.0.1/enable?auth-token=TOKEN](http://127.0.0.1/enable?auth-token=TOKEN): dial unix /var/snap/canonical-livepatch/17/livepatchd-priv.sock: connect: no such file or directory

Log file looks like this
Jan 10 08:03:57 cfkvm03 systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Main process exited, code=exited, status=1/FAILURE
Jan 10 08:03:57 cfkvm03 kernel: [154491.374821] audit: type=1400 audit(1484053437.147:60): apparmor="DENIED" operation="exec" profile="snap.ca$
Jan 10 08:03:57 cfkvm03 systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Unit entered failed state.
Jan 10 08:03:57 cfkvm03 systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Failed with result 'exit-code'.
Jan 10 08:03:57 cfkvm03 systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Service hold-off time over, scheduling restart.
Jan 10 08:03:57 cfkvm03 systemd[1]: Stopped Service for snap application canonical-livepatch.canonical-livepatchd.
Jan 10 08:03:57 cfkvm03 systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Start request repeated too quickly.
Jan 10 08:03:57 cfkvm03 systemd[1]: Failed to start Service for snap application canonical-livepatch.canonical-livepatchd.
Jan 10 08:03:57 cfkvm03 /usr/lib/snapd/snapd[15247]: daemon.go:172: DEBUG: uid=0;@ POST /v2/snaps 1.633266353s 202
Jan 10 08:03:57 cfkvm03 snap[15224]: #015#033[KAll snaps up to date.

Jan 10 08:03:57 cfkvm03 systemd[1]: Started Automatically refresh installed snaps.
Jan 10 08:03:57 cfkvm03 systemd[1]: snapd.refresh.timer: Adding 1h 35min 32.884923s random time.
Jan 10 08:03:57 cfkvm03 systemd[1]: snapd.refresh.timer: Adding 1h 19min 40.859198s random time.
Jan 10 08:04:04 cfkvm03 /usr/lib/snapd/snapd[15247]: api.go:873: Installing snap "canonical-livepatch" revision unset
Jan 10 08:04:04 cfkvm03 snapd[15247]: 2017/01/10 08:04:04.557836 api.go:873: Installing snap "canonical-livepatch" revision unset
Jan 10 08:04:04 cfkvm03 /usr/lib/snapd/snapd[15247]: daemon.go:172: DEBUG: uid=0;@ POST /v2/snaps/canonical-livepatch 1.210343ms 400

Not sure where to go from here,

Thanks in advance for your help.

---

