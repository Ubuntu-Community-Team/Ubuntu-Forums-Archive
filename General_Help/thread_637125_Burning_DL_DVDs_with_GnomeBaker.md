---
title: "Burning DL DVDs with GnomeBaker"
date: 2007-12-10
forum: General Help
---

### Post by RockinFox on 2007-12-10
I have a sony Vaio laptop with a SONY DVD RW AW-G540A drive and I am running gutsy. Recently I downloaded a dmg file of Leopard (it is a 6.8Gb File) and I am attempting to burn it to a Dual layer DVD so that I can in in stall it on my Dad's Mac. However I try to burn a it through GnomeBaker (having the "8.5GB DVD" option selected) I get the following error:

"Executing 'genisoimage -gui -V GnomeBaker data disk -A GnomeBaker -p William Wrede -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-wil/gnomebaker-8K7P2T | builtin_dd of=/dev/sr0 obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
File /home/wil/.dc++/Downloads/osx-leopard105.dmg is larger than 4GiB-1.
-allow-limited-size was not specified. There is no way do represent this file size. Aborting.
:-( write failed: Input/output error

I cannot find any place to change the size settings and I am almost positive that my drive is capable of writing DL DVDs. I'm a bit in the dark when it comes to fixing things in linux so if anyone could lend a hand that would be wonderful.

---

### Post by LaRoza on 2007-12-10
dmg files are for Macs, you will need a converter for Linux and/or Windows. It is not an ISO.

---

### Post by RockinFox on 2007-12-10
Right, but I dont think that will solve the problem, I also get an error when i try to burn cds:

"No space left on the resource.gstfilesink.c(475): gst_file_sink_render (): /gnomebaker-convert-to-wav-pipeline/file-outInternal data flow error.gstbasesrc.c(1816): gst_base_src_loop (): /gnomebaker-convert-to-wav-pipeline/file-source:
streaming task paused, reason error (-5)No space left on the resource.gstfilesink.c(475): gst_file_sink_render (): /gnomebaker-convert-to-wav-pipeline/file-outError while seeking in file "/tmp/GnomeBaker-wil/create_audiocd/gbtrack_10.wav".gstfilesink.c(414): gst_file_sink_event (): /gnomebaker-convert-to-wav-pipeline/file-out:
system error: No space left on deviceNo space left on the resource.gstfilesink.c(475): gst_file_sink_render (): /gnomebaker-convert-to-wav-pipeline/file-outError while writing to file "/tmp/GnomeBaker-wil/create_audiocd/gbtrack_10.wav".gstfilesink.c(421): gst_file_sink_event (): /gnomebaker-convert-to-wav-pipeline/file-out:
system error: No space left on device" (i am positive that it is a blank cd)

---

### Post by RockinFox on 2007-12-10
Nevermind ignore that last post

---

