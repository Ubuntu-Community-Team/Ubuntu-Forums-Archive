---
title: "[SOLVED] disc copying errors: pls help a n00b."
date: 2008-06-06
forum: General Help
---

### Post by the badger on 2008-06-06
i've got a disc to install winXP and i'm trying to burn a copy. i've been running on pure ubuntu for over a year now [!] and i'd like to set up a dual boot. i have to return the winXP disc to the library asap and don't want to install windows without having a handy disk of my own for re-installation (when it inevitably goes awry).

i've tried burning a copy by right-click->"Copy Disk..." on the icon. failed in the writing stage [dvd-r]. then i tried opening brasero from the terminal so i could perhaps get some insight. it failed again [new cd-rw], and this was the log (in brasero - terminal shows nothing):
```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
BraseroMd5sumFile called brasero_job_get_output_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile deactivating
BraseroMd5sumFile called brasero_job_get_output_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_input_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_set_current_action
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_error
BraseroMd5sumFile finished with an error
BraseroMd5sumFile asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroMd5sumFile stopping
Session error : unknown (brasero_burn_record burn.c:2273)

```

does anyone knows anything about windows that might shed some light on why the disk won't copy? is there a protected something or other keeping me from copying the disk? i can see the contents...


(or if anyone can tell me how to "copy disk" from terminal i might get a more insightful log) 

any help is, as always, most appreciated :)

---

### Post by tomcheng76 on 2008-06-06
I think you can give k3b a try (i bet it is the best burning tool in lunux :))
to install k3b:
```

sudo apt-get update
sudo apt-get install k3b

```

btw, you need cdr (not dvdr), i believe that your XP disc is cdrom (not dvdrom)

---

### Post by the badger on 2008-06-06
> **tomcheng76 said:**
> I think you can give k3b a try (i bet it is the best burning tool in lunux :))

i totally agree, tomcheng76! i just haven't installed it since i've been using the heron.

i think my problem might have had something to do with file permissions(?) since copying all files to my HD and changing the permissions has allowed me to then burn the disc using brasero. 
...now on to set up the dual-boot!

---

