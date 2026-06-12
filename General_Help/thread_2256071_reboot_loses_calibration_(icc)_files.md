---
title: "reboot loses calibration (*icc) files"
date: 2014-12-09
forum: General Help
---

### Post by jamzen on 2014-12-09
On every boot I have to reselect the calibration file for my right-hand monitor.  I originally calibrated them two days ago, via the Color dialog.  I've verified the *.icc file corresponding to each monitor.  But at boot time I have to go back to that same dialog box and reselect the file.  Until I do that, the monitors exhibit the same uncalibrated color values they did last week.

That's a PIA.

I use two monitors, an HP w2207 and HP LV2311, and Nvidia-settings to integrate them.

There's a file for each one in /var/lib/colord/icc:
     GCM - Hewlett Packard - HP LV2311 - 6CM24100RW (2014-12-07) [13-29-13].icc
     GCM - Hewlett Packard - HP w2207 - CND72632C3 (2014-12-07) [11-45-41].icc

Why isn't the calibration "sticking" between boots?

---

