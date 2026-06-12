---
title: "Disabling (temporarily) Compiz effects ?"
date: 2012-12-05
forum: General Help
---

### Post by cogset on 2012-12-05
Hi,I'd need to know if there's any way to only temporarily disable all  Compiz advanced effects,as I have  compiz-fusion-plugins-extra   installed with effects as desktop cube,wobbly windows,expo,and so on  enabled,and I need to troubleshoot a rendering issue that I have never  experienced in another Lucid installation without the advanced effects:I  reckon there's no quick toggle,not at least in the Compiz manager  GUI,to do this.
Can it be done from the terminal,or do I have to  uncheck every option in the settings manager ? I'd basically want to  temporarily revert to just basic desktop effects,to see if that  rendering issue still surfaces.

---

### Post by Isamu715 on 2012-12-05
So, basically you want to temporarily disable Compiz. You mentioned you're on Lucid so the following line should do:
```
metacity --replace
```

---

