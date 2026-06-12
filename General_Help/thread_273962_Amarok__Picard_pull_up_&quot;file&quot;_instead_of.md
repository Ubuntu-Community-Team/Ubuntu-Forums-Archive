---
title: "Amarok / Picard pull up &quot;file:///&quot; instead of Musicbrainz webpage."
date: 2006-10-09
forum: General Help
---

### Post by Cronjob on 2006-10-09
:: Kubuntu Dapper (6.06) AMD64 ::

When playing a song in amarok, there is a little musicbrainz icon you can click on. Also, in the musicbrainz 'picard' application, you click the 'lookup' button in the process of identifying your albums.

When I click on the musicbrainz link from amarok or the lookup button in picard, I am directed to a link like this in my browser:

file:///var/tmp/kdecache-cronjob/krun/9876.0.taglookup.html

Which is completely useless, because it's just a css-stripped file with no links to the musicbrainz website or database, rendering all navigation and selection non-functional.

I can't find anything about this on the amarok website, in the forums here or elsewhere via google. Any ideas?!

---

### Post by Cronjob on 2006-10-10
Apologies for bumping this (I originally posted this at a very off hour, I know) but I'm hoping someone can offer me a little help on this. I believe the problem is something in the way KDE is handling links/handoffs rather than something with Amarok / Picard / Musicbrainz. These are the only applications that pull up "file:///" with a link to the local kde-cache under my user account instead of "http:///" pointing at the actual data on the website, but I'm not sure how to correct this.

Any guidance would be very appreciated. I have about 42,000 files that need to be organized and without musicbrainz, I am never going to accomlish that! :)

---

### Post by luks on 2006-10-11
What browser have you set as the default one? The command for launching browser for example for Firefox should be "firefox %U".

---

### Post by Cronjob on 2006-10-11
> **luks said:**
> What browser have you set as the default one? The command for launching browser for example for Firefox should be "firefox %U".

Ah, yep. That did it. For some reason, there was no "%u" at the end. That didn't even occur to me since some links worked just fine (for example, clicking on the album cover in Amarok sends you to Amazon. Clicking on the musicbrainz icon an inch to the right send you to the kde-cache thing).

Thank you, very much. :)

---

