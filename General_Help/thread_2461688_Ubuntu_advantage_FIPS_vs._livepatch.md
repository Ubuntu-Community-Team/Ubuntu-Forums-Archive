---
title: "Ubuntu advantage: FIPS vs. livepatch"
date: 2021-05-05
forum: General Help
---

### Post by cbraxton on 2021-05-05
I went ahead and registered my 16.04 desktop system for Ubuntu Advantage since I don't have time right now to redo everything. When first running "ua attach [token]", the process hung for quite some time then came back with this result:

```

Enabling default service esm-infra
Updating package lists

Enabling default service livepatch
Installing canonical-livepatch snap
Canonical livepatch enabled.
Failed to enable default services, check: sudo ua status

```

Running "sudo ua status" comes up with:

```

SERVICE       ENTITLED   STATUS    DESCRIPTION
esm-infra     yes        disabled  UA Infra: Extended Security Maintenance (ESM)
fips          yes        disabled  NIST-certified FIPS modules
fips-updates  yes        disabled  Uncertified security updates to FIPS modules
livepatch     yes        enabled   Canonical Livepatch service

```

I successfully enabled esm-infra using "sudo ua enable esm-infra". So now esm-infra and livepatch have been successfully enabled.

```

SERVICE       ENTITLED   STATUS    DESCRIPTION
esm-infra     yes        enabled   UA Infra: Extended Security Maintenance (ESM)
fips          yes        disabled  NIST-certified FIPS modules
fips-updates  yes        disabled  Uncertified security updates to FIPS modules
livepatch     yes        enabled   Canonical Livepatch service

```

However, attempting to enable fips results in the following message:

```

Installation of additional packages are required to make this system FIPS
compliant.
Are you sure? (y/N) y
FIPS cannot be enabled with Livepatch.
Disable Livepatch and proceed to enable FIPS? (y/N)
Cannot enable FIPS when Livepatch is enabled.

```

Would the "default services" have included all four services had the initial run completed successfully? Should I enable the fips services in preference to livepatch? (This is my first experience with Ubuntu Advantage.)

---

### Post by deadflowr on 2021-05-05
Does this help?
[https://security-certs.docs.ubuntu.com/en/fips-faq]("https://security-certs.docs.ubuntu.com/en/fips-faq")

---

### Post by cbraxton on 2021-05-05
Thanks, looks like FIPS is not anything needed for an ordinary desktop system. I'll leave things as they are until I have time to install a newer Ubuntu version.

---

