---
title: "f-spot &quot;database locked&quot; on cropping photo"
date: 2007-03-17
forum: General Help
---

### Post by carljm on 2007-03-17
Hi everyone,

Just in the last few days I've started getting a "database locked" error occasionally when I try to crop a photo in F-Spot.  (After I get the error there's a tiny modal dialog with nothing in it which is difficult to see, but I have to find it and close it before I can close F-Spot).  When I shut down F-Spot and examine my photo directory and the sqlite database, the cropped version of the photo has been created and the "photos" table has been updated with a new default_version_id, but there is no corresponding entry in the photo_versions table.

I'm using F-Spot 0.1.11 (the most recent version available for Dapper) under Gnome.

I have no idea if this is relevant, but the problem seemed to appear right around the same time that I installed Beagle and gDesklets.

I've googled and searched for this issue to no avail.  Anyone have a clue how I can fix this?

Many thanks in advance, and apologies if this is the wrong forum for this query.

Carl

---

