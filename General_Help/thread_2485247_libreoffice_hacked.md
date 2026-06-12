---
title: "libreoffice hacked?"
date: 2023-03-24
forum: General Help
---

### Post by Old Jimma on 2023-03-24
Hello Forum:

There are several websites that have indicated tht Libreoffic was hacked in previous versions.

Here is one: [https://thehackernews.com/2019/07/libreoffice-vulnerability.html](https://thehackernews.com/2019/07/libreoffice-vulnerability.html)

Here is another: [https://ask.libreoffice.org/t/was-my-libreoffice-hacked-or-accessed-by-outside-third-party/22621](https://ask.libreoffice.org/t/was-my-libreoffice-hacked-or-accessed-by-outside-third-party/22621)

A few days ago I posted a query about odd behavior of Libreoffice calc on Ubuntuforums.org: [https://ubuntuforums.org/showthread.php?t=2485223&p=14136020#post14136020](https://ubuntuforums.org/showthread.php?t=2485223&p=14136020#post14136020)


Ordinarily, I receive several very good responses to my queries on ubuntuforums.org within 24 hours. 

However, I've gotten no response to this query.


So, for the sake of the ubuntu community, I thought I should get this out in the open so that it could be settled.... and dismissed... provided there are authoritive responses to the query. If there is a hack, it doesn't make sense to keep it secret. If there was not a hack, let's discuss this, and bury the issue.

If there wasn't a hack, why did I get this yesterday morning: [https://ubuntuforums.org/showthread.php?t=2485223&p=14136020#post14136020](https://ubuntuforums.org/showthread.php?t=2485223&p=14136020#post14136020)

I'm not the type of guy who screams "Fire" in a crowded theater. Just looking out for myself, and the community that has graciously helped me so many times since 6.04

Sincerely,
Old

I hoop

---

### Post by kingpenguin on 2023-03-28
I was able to find this website [https://nvd.nist.gov/vuln/detail/CVE-2019-9848](https://nvd.nist.gov/vuln/detail/CVE-2019-9848) which shows that 3 versions of ubuntu were effected by this CVE. This does not mean that your computer is guarnteed to have malware if you have one of these versions of libreoffice. You still have to open a specially crafted document that was sent to you. Does this answer your question?

---

### Post by ian-weisser on 2023-03-28
> **Old Jimma said:**
> Hello Forum:

There are several websites that have indicated tht Libreoffic was hacked in previous versions.


Random websites often spread FUD. Real vulnerabilities are reported and assigned CVE numbers. Look for the CVE numbers.

For example, an authoritative source for Libreoffice vulnerabilities is [https://www.libreoffice.org/about-us/security/advisories/](https://www.libreoffice.org/about-us/security/advisories/), which pairs each vulnerability with a CVE.
Example: [CVE-2022-26305]("https://www.libreoffice.org/about-us/security/advisories/cve-2022-26305/") Execution of Untrusted Macros Due to Improper Certificate Validation

The Ubuntu Security Team tracks those CVEs, rebuilds the packages with patches, and pushes those patches into the -security repo.
Example: [https://ubuntu.com/security/cves?q=CVE-2022-26305](https://ubuntu.com/security/cves?q=CVE-2022-26305)
18.04 Fix Released in version 1:6.0.7-0ubuntu0.18.04.12
20.04 Fix Released in version 1:6.4.7-0ubuntu0.20.04.5
22.04 Not Vulnerable
22.10 Not Vulnerable

And, of course, your system --if setup correctly-- checks the -security repo about twice daily.

If you believe that your LibreOffice was hacked, the first place to go is [https://www.libreoffice.org/about-us/security/](https://www.libreoffice.org/about-us/security/) . Let the LibreOffice security experts verify the vulnerability and then assign a CVE.

---

