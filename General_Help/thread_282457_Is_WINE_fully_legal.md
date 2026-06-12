---
title: "Is WINE fully legal?"
date: 2006-10-22
forum: General Help
---

### Post by paul6 on 2006-10-22
Is WINE, and all the software Winetools installs with it, 100% legal? I  **don't** own a Windows license, so I'd just like to make sure this is ok to install.

---

### Post by raul_ on 2006-10-22
> **Microsoft's response to Wine**

Microsoft has generally not made public statements about Wine. However, the Microsoft Update software will block updates to Microsoft application software running in Wine-based environments. On February 16, 2005, Ivan Leo Puoti discovered that Microsoft had started checking the Windows registry for the Wine configuration key and would block the Windows Update for any component. Puoti wrote, "... even if this is only an initial attempt, they appear to want to discriminate against Wine users. While this may be acceptable for operating system components/updates, this is probably a violation of anti-trust law for all other downloads. It's also the first time Microsoft has acknowledged the existence of Wine."[6]

The Windows Genuine Advantage (WGA) system also checks for existence of Wine registry keys, and the WGA FAQ states that WGA, by design, will not run in Wine, as Wine does not constitute "genuine Windows" as described in the WGA FAQ: "When WGA validation detects WINE running on the system, it will notify users that they are running non-genuine Windows, and it will not allow genuine Windows downloads for that system".[7] Despite this, some reports have circulated of the WGA system working in Wine nevertheless.[8] It must be noted, however, that MS' WGA FAQ also states "It is important to note that Wine users, and other users of non-genuine Windows, can continue to download updates for most Microsoft applications from Microsoft application-specific sites, such as Office Update", affirming MS' position as neutral to Wine but not wishing to offer support for it.

The beta version of Microsoft Internet Explorer 7 checks at installation-time for WGA, and hence users cannot install it on Linux systems which use Wine, without modifying the Internet Explorer setup files or Wine itself.

From [http://en.wikipedia.org/wiki/Wine_%28software%29#Microsoft.27s_response_to_Wine]("http://en.wikipedia.org/wiki/Wine_%28software%29#Microsoft.27s_response_to_Wine")

---

### Post by skymt on 2006-10-22
Wine is really, fully, 100% legal. It's a from-scratch re-implementation of the Windows core ("core" meaning certain essential components needed to run applications). It has no code or binary data from Microsoft's implementation.

---

