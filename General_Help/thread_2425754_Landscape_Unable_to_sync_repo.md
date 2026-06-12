---
title: "Landscape: Unable to sync repo"
date: 2019-08-29
forum: General Help
---

### Post by mrinal29 on 2019-08-29
I am trying to setup Landscape and facing some issue in syncing repository.
I followed [https://docs.ubuntu.com/landscape/en/landscape-install-quickstart](https://docs.ubuntu.com/landscape/en/landscape-install-quickstart) and all that I did is:


#add-apt-repository ppa:landscape/19.01
#apt-get install landscape-server-quickstart
#lsctl restart
#apt-get install rng-tools && sudo rngd -r /dev/urandom
#gpg --gen-key
# gpg -K
/root/.gnupg/pubring.kbx
------------------------
sec   rsa3072 2019-08-29 [SC] [expires: 2021-08-28]
      60097EF6E9DB685FE42EEAF61B9B9012DE7B81A0
uid           [ultimate] Mirror Key
ssb   rsa3072 2019-08-29 [E] [expires: 2021-08-28]
#gpg -a --export-secret-keys 60097EF6E9DB685FE42EEAF61B9B9012DE7B81A0 > mirror-key.asc
#landscape-api import-gpg-key mirror-key mirror-key.asc
#landscape-api create-distribution ubuntu
#landscape-api create-series --pockets release,updates,security --components main,restricted,universe,multiverse --architectures amd64,i386 --gpg-key mirror-key --mirror-uri [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) --mirror-series bionic bionic ubuntu
#landscape-api sync-mirror-pocket release bionic ubuntu


#landscape-api get-activities --query id:4
[{u'activity_status': u'undelivered',
  u'children': [],
  u'completion_time': None,
  u'creation_time': u'2019-08-29T15:18:56Z',
  u'creator': {u'email': u'xyz@abc.com',
               u'id': 1,
               u'name': u'c183983'},
  u'id': 4,
  u'modification_time': u'2019-08-29T15:18:56Z',
  u'parent_id': 3,
  u'pocket_id': 1,
  u'pocket_name': u'release',
  u'progress': 0,
  u'result_code': None,
  u'result_text': None,
  u'schedule_after_time': None,
  u'schedule_before_time': None,
  u'summary': u"Sync pocket 'release' of series 'bionic' in distribution 'ubuntu'",
  u'type': u'SyncPocketRequest'}]


I have the proxy configured.
# cat /etc/apt/apt.conf
Acquire::http::Proxy "http://c123456:password@40.0.40.10:9000";
Acquire::https::Proxy "http://c123456:password@40.0.40.10:9000";
  
I have 3 isues here:
1.	The repository sync stays in queued state and did not starts. What am I missing here?


2.	landscape-package-search always stays in failed state.


# systemctl status landscape-package-search
&#9679; landscape-package-search.service - Landscape's Package Search daemon
   Loaded: loaded (/lib/systemd/system/landscape-package-search.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Thu 2019-08-29 11:42:41 EDT; 4min 29s ago
  Process: 10499 ExecStart=/opt/canonical/landscape/package-search (code=exited, status=1/FAILURE)
  Process: 10473 ExecStartPre=/opt/canonical/landscape/landscape-schema-check (code=exited, status=0/SUCCESS)
 Main PID: 10499 (code=exited, status=1/FAILURE)


Aug 29 11:42:41 devdl360gen1001 systemd[1]: landscape-package-search.service: Service hold-off time over, scheduling restart.
Aug 29 11:42:41 devdl360gen1001 systemd[1]: landscape-package-search.service: Scheduled restart job, restart counter is at 20.
Aug 29 11:42:41 devdl360gen1001 systemd[1]: Stopped Landscape's Package Search daemon.
Aug 29 11:42:41 devdl360gen1001 systemd[1]: landscape-package-search.service: Start request repeated too quickly.
Aug 29 11:42:41 devdl360gen1001 systemd[1]: landscape-package-search.service: Failed with result 'exit-code'.
Aug 29 11:42:41 devdl360gen1001 systemd[1]: Failed to start Landscape's Package Search daemon.
Aug 29 11:46:45 devdl360gen1001 systemd[1]: landscape-package-search.service: Start request repeated too quickly.
Aug 29 11:46:45 devdl360gen1001 systemd[1]: landscape-package-search.service: Failed with result 'exit-code'.
Aug 29 11:46:45 devdl360gen1001 systemd[1]: Failed to start Landscape's Package Search daemon.


3.	landscape-pppa-proxy is not installed by default. Do I need it?

---

