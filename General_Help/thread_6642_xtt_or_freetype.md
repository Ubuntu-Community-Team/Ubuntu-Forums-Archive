---
title: "xtt or freetype"
date: 2004-11-30
forum: General Help
---

### Post by istoyanov on 2004-11-30
Since I've been told that there should be only one of the modules "xtt" or "freetype" enabled in XF86Config-4 (the default after a clean install is both of them loaded), here I would like to ask you which should be the preferred way to handle TrueType fonts in Xfree86?

Thank you in advance!

Cheers,

IS

Meanwhile I found on xfree86.org the following information:

-----
* "freetype": TrueType fonts (`*.ttf' and `*.ttc'), OpenType fonts (`*.otf' and `*.otc') and Type 1 fonts (`*.pfa' and `*.pfb');
* "type1": alternate Type 1 backend (`*.pfa' and `*.pfb') and CIDFont backend;
* "xtt": alternate TrueType backend (`*.ttf' and `*.ttc');
-----

Can this be a hint on using "freetype" as the primary font-rendering tool, thus disabling "type1" and "xtt" in the configuration file?

---

