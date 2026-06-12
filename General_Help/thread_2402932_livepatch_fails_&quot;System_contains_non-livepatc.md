---
title: "livepatch fails: &quot;System contains non-livepatch tainted modules.&quot;"
date: 2018-10-05
forum: General Help
---

### Post by ingenium2 on 2018-10-05
I finally have livepatch setup, but it fails to apply. Looking through my systemd logs, I see the following:
```
Oct 05 13:29:56 josh-ThinkPad-T460 canonical-livepatch[16571]: Client.CheckOct 05 13:29:56 josh-ThinkPad-T460 canonical-livepatch[16571]: Checking with livepatch service.
Oct 05 13:29:57 josh-ThinkPad-T460 canonical-livepatch[16571]: updating last-check
Oct 05 13:29:57 josh-ThinkPad-T460 canonical-livepatch[16571]: touched last check
Oct 05 13:29:57 josh-ThinkPad-T460 canonical-livepatch[16571]: No updates available at this time.
Oct 05 13:29:57 josh-ThinkPad-T460 canonical-livepatch[16571]: System contains non-livepatch tainted modules.
Oct 05 13:29:57 josh-ThinkPad-T460 canonical-livepatch[16571]: Module may have caused kernel crash! Not inserting module.
Oct 05 13:29:57 josh-ThinkPad-T460 canonical-livepatch[16571]: To override this warning remove: /var/snap/canonical-livepatch/common/locks/livepatch_Ubuntu_4_15_0_34_37_generic_44
Oct 05 13:29:57 josh-ThinkPad-T460 canonical-livepatch[16571]: during refresh: cannot apply patches: lock file exists: /var/snap/canonical-livepatch/common/locks/[COLOR=#000000]livepatch_Ubuntu_4_15_0_34_37_generic_44_44.1[/COLOR]
```

I deleted /var/snap/canonical-livepatch/common/locks/[COLOR=#000000]livepatch_Ubuntu_4_15_0_34_37_generic_44_44.1, but it just gets re-created an hour later when livepatch tries to apply again. 

I checked, and the only tainted kernel modules that I have are from nvidia proprietary drivers:
[/COLOR]```
nvidia_uvm
nvidia_drm
nvidia_modeset
nvidia
```[COLOR=#000000]
I believe that these use dkms, so they shouldn't be a problem for livepatch to rebuild them for the new kernel, correct? Is there something else that I need to do to get this to work?
[/COLOR]

---

