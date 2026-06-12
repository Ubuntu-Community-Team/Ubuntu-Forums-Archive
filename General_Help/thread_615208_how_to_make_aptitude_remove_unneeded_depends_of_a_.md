---
title: "how to make aptitude remove unneeded depends of a metapackage"
date: 2007-11-16
forum: General Help
---

### Post by maybeway36 on 2007-11-16
Here is the default /etc/apt/apt.conf.d/01autoremove:
```
APT
{
  NeverAutoRemove  
  { 
	"^linux-image.*";  
	"^linux-restricted-modules.*";
	"^linux-ubuntu-modules-.*";
  };

  Never-MarkAuto-Sections
  { 
	"metapackages";
        "restricted/metapackages";
        "universe/metapackages";
        "multiverse/metapackages";
  };
};


```
You need to change it to:
```
APT
{
  NeverAutoRemove  
  { 
	"^linux-image.*";  
	"^linux-restricted-modules.*";
	"^linux-ubuntu-modules-.*";
  };
};


```

---

