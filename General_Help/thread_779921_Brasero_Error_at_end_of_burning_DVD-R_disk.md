---
title: "Brasero Error at end of burning DVD-R disk"
date: 2008-05-03
forum: General Help
---

### Post by FixedSys on 2008-05-03
The disk finishes and is showing 100% of the data on the disk but the error pops up right at the end of the burn. (once it reaches 100%)  This is reflected in the error log.  Here is the last part of the log:

```
BraseroGrowisofs stderr:  99.77% done, estimate finish Sat May  3 02:55:57 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr: Total translation table size: 0
BraseroGrowisofs stderr: Total rockridge attributes bytes: 1546
BraseroGrowisofs stderr: Total directory bytes: 0
BraseroGrowisofs stderr: Path table size(bytes): 10
BraseroGrowisofs stderr: Done with: The File(s)                             Block(s)    2154873
BraseroGrowisofs stderr: Writing:   Ending Padblock                         Start Block 2154905
BraseroGrowisofs stderr: Done with: Ending Padblock                         Block(s)    150
BraseroGrowisofs stderr: Max brk space used 0
BraseroGrowisofs stderr: 2155055 extents written (4209 MB)
BraseroGrowisofs stderr: /dev/scd1: flushing cache
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: :-( unable to FLUSH CACHE: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Unhandled error, aborting"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : Unhandled error, aborting (brasero_burn_record burn.c:2270)
```

This is an external Pioneer USB 2.0 drive.  Ubuntu Hardy 8.04
It trying to flush cache of device? Permissions issue maybe?

---

### Post by FixedSys on 2008-05-03
:guitar:

Installed GnomeBaker and that program worked with out any errors!
It was the Brasero application that had the problem.
GnomeBaker should be the default cd/dvd burner client and not Brasero.  
Brasero is not even able to burn Dual Layer Media! (But GnomeBaker does that just fine.)

---

