---
title: "EasyTAG truncating FLAC dates?"
date: 2007-10-29
forum: General Help
---

### Post by Slim Backwater on 2007-10-29
I'm ripping my CD collection with Sound Juicer (in Feisty) to FLAC and I use EasyTag for editing tags.

I thought I'd check the tags in EasyTag and clicking through easy file turned the file red, as if I had changed something, but I hadn't.

I compared a copy of the flac to the resaved one with metaflac -list and it seems that the date tag has been truncated to just a simple year, while the original has a year-month-day format.

I don't even know how SoundJuicer is getting these exact dates, but editing them in FLAC truncates it to just a year.

I can't find out if Sound Juice is making a bad tag (against the format for the DATE tag) or if EasyTag has a bug that's truncating it to just the first 4 digits.

Here's a before and after look with metaflac --list
```

METADATA block #0
  type: 0 (STREAMINFO)
  is last: false
  length: 34
  minumum blocksize: 4608 samples
  maximum blocksize: 4608 samples
  minimum framesize: 14 bytes
  maximum framesize: 15839 bytes
  sample_rate: 44100 Hz
  channels: 2
  bits-per-sample: 16
  total samples: 9935436
  MD5 signature: 92a545a0f79a090491cb865e10f9dc12
METADATA block #1
  type: 4 (VORBIS_COMMENT)
  is last: true
  length: 526
  vendor string: reference libFLAC 1.1.2 20050205
  comments: 13
    comment[0]: TITLE=Underneath Your Clothes
    comment[1]: ARTIST=Shakira
    comment[2]: TRACKNUMBER=2
    comment[3]: TRACKTOTAL=13
    comment[4]: ALBUM=Shakira-Laundry Service
    comment[5]: MUSICBRAINZ_ALBUMID=46f25a39-1630-4bed-8b5c-5aef1e464757
    comment[6]: MUSICBRAINZ_ALBUMARTISTID=bf24ca37-25f4-4e34-9aec-460b94364cfc
    comment[7]: MUSICBRAINZ_ARTISTID=bf24ca37-25f4-4e34-9aec-460b94364cfc
    comment[8]: MUSICBRAINZ_TRACKID=b7ba747b-f975-40a2-948b-0c064299aff9
    comment[9]: MUSICBRAINZ_SORTNAME=Shakira
    comment[10]: DATE=2001-11-13
    comment[11]: DISCID=b10b8f0d
    comment[12]: MUSICBRAINZ_DISCID=Zvn68oNsUBub_Djmcuvzh6WsJJ8-

```

After clicking/saving in EasyTag
```

METADATA block #0
  type: 0 (STREAMINFO)
  is last: false
  length: 34
  minumum blocksize: 4608 samples
  maximum blocksize: 4608 samples
  minimum framesize: 14 bytes
  maximum framesize: 15839 bytes
  sample_rate: 44100 Hz
  channels: 2
  bits-per-sample: 16
  total samples: 9935436
  MD5 signature: 92a545a0f79a090491cb865e10f9dc12
METADATA block #1
  type: 4 (VORBIS_COMMENT)
  is last: false
  length: 521
  vendor string: reference libFLAC 1.1.2 20050205
  comments: 13
    comment[0]: TITLE=Underneath Your Clothes
    comment[1]: ARTIST=Shakira
    comment[2]: ALBUM=Shakira-Laundry Service
    comment[3]: DATE=2001
    comment[4]: TRACKNUMBER=02
    comment[5]: TRACKTOTAL=13
    comment[6]: MUSICBRAINZ_ALBUMID=46f25a39-1630-4bed-8b5c-5aef1e464757
    comment[7]: MUSICBRAINZ_ALBUMARTISTID=bf24ca37-25f4-4e34-9aec-460b94364cfc
    comment[8]: MUSICBRAINZ_ARTISTID=bf24ca37-25f4-4e34-9aec-460b94364cfc
    comment[9]: MUSICBRAINZ_TRACKID=b7ba747b-f975-40a2-948b-0c064299aff9
    comment[10]: MUSICBRAINZ_SORTNAME=Shakira
    comment[11]: DISCID=b10b8f0d
    comment[12]: MUSICBRAINZ_DISCID=Zvn68oNsUBub_Djmcuvzh6WsJJ8-
METADATA block #2
  type: 1 (PADDING)
  is last: true
  length: 1

```

I also now that EasyTag is adding a Metadata block 2 (PADDING), I don't know if that's a problem or not.

Who know how many files I've tagged in easytag, it seems like a really nice program, and I'd hate to have to stop using it if it's borking up FLAC files.

Any Ideas?

Thanks.

---

