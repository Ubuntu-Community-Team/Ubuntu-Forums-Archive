---
title: "gDesklets Errors"
date: 2006-11-17
forum: General Help
---

### Post by norcalnewb on 2006-11-17
I have installed gdesklets, but anytime I try to add a new desklet, I get an error:

No Control could be found for interface IYahooWeather:0nhnha8qm4hqxw6b6rwffr5e0-2

I can't seem to get any of these to work.  I am downloading the desklets from [www.gdesklets.org](www.gdesklets.org).

I cannot get any of the weather desklets to connect to a source for the weather information either.  I can't seem to find any documentation regarding gDesklets.  Does anybody know where documentation is located?

Thanks.

---

### Post by computx on 2006-11-17
You should probably rm -rf ~/.gdesklets to get rid of the error message about yahooweather. That will cause gdesklets to generate a new profile for you.

As for the gdesklet weather applets not connecting it is because almost all of them grab weather from yahoo and yahoo changed their weather page format.

I did try one gdesklet, iweather that worked but I believe it is no longer being developed and is hard to find plus it was designed for an earlier version of gdesklets.

---

