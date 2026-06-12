---
title: "numbering text file"
date: 2007-12-31
forum: General Help
---

### Post by dancer58 on 2007-12-31
I have a text file with appr. 1000 lines, Over 60% have the same name. One thing in common with all the lines are the letters, in caps, COE. Does anyone know a way to number each line by putting a number at the end of "COE" starting with 1 and incrementing by 1 for each line in the file. "COE" is not in the same place on each line.

This is a points of interest (POI) for Roadmap program.

I have tried googling but found nothing and don't know where to go

Any help is appreciated

Thanks
Harold

---

### Post by ghostdog74 on 2007-12-31
```
awk '{print $0,++c}' file

```

---

### Post by geirha on 2007-12-31
Could you post some example lines, and how the lines should look afterwards?

---

