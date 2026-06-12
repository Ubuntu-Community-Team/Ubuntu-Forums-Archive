---
title: "mtp-detect help please"
date: 2008-01-29
forum: General Help
---

### Post by maddbaron on 2008-01-29
I just got a zen plus v whenever i connect it via the usb I get a msg saying the usb device cannot be claimed after it views it as a camera when its an mp3 player...I installed the gnomad2 and the the code to make it work with amarok but still can't get it to work.


I figure if I can get ubuntu to claim the usb device I should be ok but it won't.

I ran mtp-detect and got this
> mtp-detect
Found non-autodetected device "Creative Zen V Plus" on USB bus...
usb_claim_interface(): Operation not permitted
Connection error.
No devices.

after searching I found these instruction on how to solve it  
[http://ubuntuforums.org/showthread.php?t=643512](http://ubuntuforums.org/showthread.php?t=643512)
but when I run gnomad2 i get the same issue...I ran mtp-detect and got a new proiblem

> mtp-detect
libmtp version: 0.2.5

Attempting to connect device(s)
usb_claim_interface(): Operation not permitted
LIBMTP PANIC: Unable to initialize device 1
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1569
Detect: There has been an error connecting. Exiting

I then ran another command I saw there and now see my device but it is still not connected in gnomad2 or amarok

> /etc/udev$ lsusb
Bus 003 Device 003: ID 041e:4152 Creative Technology, Ltd
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


I ran dmesg but I don't understand what is is I am reading...

Can someone please help me get it connected please?

---

### Post by FuturePilot on 2008-01-29
If it's asking you to import photos click cancel. That might be making everything else act a bit quirky when it tries to load it as a camera.

---

### Post by maddbaron on 2008-01-29
I ran sudo mtp-detect and got this I see a lot of read only's is this a permission problem?

> sudo mtp-detect
Password:
libmtp version: 0.2.5

Attempting to connect device(s)
PTP: Opening session
Detect: Successfully connected 1 devices
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 255
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 041e
   idProduct: 4152
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Device flags: 0x00000000
Microsoft device descriptor 0xee:
        0000: 1203 4d00 5300 4600 5400 3100 3000 3000   ..M.S.F.T.1.0.0.
        0010: fe00                                      ..
Microsoft device response to control message 1, CMD 0xfe:
        0000: 2800 0000 0001 0400 0100 0000 0000 0000   (...............
        0010: 0001 4d54 5000 0000 0000 0000 0000 0000   ..MTP...........
        0020: 0000 0000 0000 0000                       ........
Microsoft device response to control message 2, CMD 0xfe:
        0000: 2800 0000 0001 0400 0100 0000 0000 0000   (...............
        0010: 0001 4d54 5000 0000 0000 0000 0000 0000   ..MTP...........
        0020: 0000 0000 0000 0000                       ........
Device info:
   Manufacturer: Creative Technology Ltd
   Model: Creative Zen V Plus
   Device version: 1.11.01_0.05.09
   Serial number: CB29418A0002FA9DCB2EE6C10002FA9D
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0;microsoft.com/WMPPD: 10.0;microsoft.com/WMDRMPD: 10.1;audible.com: 1.0;
   Detected object size: 64 bits
Supported operations:
   1001: get device info
   1002: Open session
   1003: Close session
   1004: Get storage IDs
   1005: Get storage info
   1007: Get object handles
   100c: Send object info
   100d: Send object
   100f: Format storage
   1014: Get device property description
   1015: Get device property value
   1006: Get number of objects
   1008: Get object info
   1009: Get object
   100b: Delete object
   1010: Reset device
   1016: Set device property value
   1017: Reset device property value
   9801: Get object properties supported
   9802: Get object property description
   9803: Get object property value
   9804: Set object property value
   9805: Get object property list
   9806: Set object property list
   9808: Send object property list
   9807: Get interdependent property description
   9810: Get object references
   9811: Set object references
   9201: Report Added/Deleted Items
   9101: Get secure time challenge
   9102: Get secure time response
   9103: Set license response
   9104: Get sync list
   9105: Send meter challenge query
   9106: Get meter challenge
   9107: Get meter response
   9108: Clean data store
   9109: Get license state
Events supported:
   None.
Device Properties Supported:
   0x5001: Battery Level
   0xd401: Synchronization Partner
   0xd402: Friendly Device Name
   0xd101: Secure Time
   0xd102: Device Certificate
   0xd201: Unknown property
Playable File (Object) Types and Object Properties Supported:
   3009: MP3
      de99: AudioWAVECodec UINT32 data type enumeration: 85,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 8000, MAX 320000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   b901: WMA
      de99: AudioWAVECodec UINT32 data type enumeration: 352, 353,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   3008: MS Wave
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   300c: ASF
      de99: AudioWAVECodec UINT32 data type enumeration: 353,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 5000, MAX 505000, STEP 1 READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   b904: Audible.com Codec
      da01: unknown(da01) UINT32 data type enumeration: 2, 3, 4,  GET/SET
      da02: unknown(da02) array of UINT16 data type ANY 16BIT VALUE form GET/SET
      da03: unknown(da03) UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc46: Artist STRING data type GET/SET
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: BuyFlag UINT8 data type ANY 8BIT VALUE form GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   ba05: Abstract Audio Video Playlist
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   ba03: Abstract Audio Album
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 112, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 20480, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 128, STEP 1 READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   3801: JPEG
      dc88: Height UINT32 data type range: MIN 0, MAX 2304, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  READ ONLY
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 170, STEP 1 READ ONLY
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX 20480, STEP 1 READ ONLY
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 170, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 3072, STEP 1 GET/SET
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   300a: MS AVI
      de99: AudioWAVECodec UINT32 data type enumeration: 17,  READ ONLY
      de9a: AudioBitRate UINT32 data type range: MIN 16000, MAX 384000, STEP 1 READ ONLY
      de9d: FramesPerThousandSeconds UINT32 data type range: MIN 6000, MAX 15000, STEP 1 READ ONLY
      dc88: Height UINT32 data type range: MIN 0, MAX 128, STEP 1 GET/SET
      de91: TotalBitRate UINT32 data type range: MIN 0, MAX 9500000, STEP 1 READ ONLY
      de9b: VideoFourCCCodec UINT32 data type enumeration: 3,  READ ONLY
      de9c: VideoBitRate UINT32 data type range: MIN 0, MAX 4000000, STEP 1 READ ONLY
      dc87: Width UINT32 data type range: MIN 0, MAX 128, STEP 1 GET/SET
      dc89: Duration UINT32 data type ANY 32BIT VALUE form GET/SET
      de93: SampleRate UINT32 data type enumeration: 8000, 11025, 12000, 16000, 22050, 24000, 32000, 44100, 48000,  READ ONLY
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  READ ONLY
      de95: AudioBitDepth UINT32 data type enumeration: 8, 16,  READ ONLY
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   bb83: vCard3
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   be03: vCalendar2
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   3000: Undefined Type
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   3001: Association/Directory
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   b802: Firmware
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003
      FilesystemType: 0x0002
      AccessCapability: 0x0000
      MaxCapacity: 971440128
      FreeSpaceInBytes: 330629120
      FreeSpaceInObjects: 4294967295
      StorageDescription: Storage Media
      VolumeIdentifier: CB29418A0002FA9DCB2EE6C10002FA9D
Special directories:
   Default music folder: 0x00000056
   Default playlist folder: 0x0000005a
   Default picture folder: 0x00000066
   Default video folder: 0x0000006a
   Default organizer folder: 0x00000062
   Default zencast folder: 0x00000000
   Default album folder: 0x00000000
   Default text folder: 0x00000000
MTP-specific device properties:
   Friendly name: My Zen
   Synchronization partner: (NULL)
   Battery level 255 of 255 (100%)
libmtp supported (playable) filetypes:
   ISO MPEG-1 Audio Layer 3
   Microsoft Windows Media Audio
   RIFF WAVE file
   Microsoft Advanced Systems Format
   Audible.com Audio Codec
   JPEG file
   Audio Video Interleave
   VCard version 3
   VCalendar version 2
   Firmware file

Secure Time:
<DRMCLOCK type="status"><VALUE>#20060321 14:27:02Z#</VALUE><FLAG>DRM_CLK_NOT_SET</FLAG></DRMCLOCK>

Device Certificate:
<DEVCERT version="1.0"><CERTIFICATE type="DEVICE"><DATA><UNIQUEID private="1">ikEpy536AgDB5i7LnfoCAAAAAAA=</UNIQUEID><PUBLICKEY private="1">9OBtM50oB4o3ZDzN1gBqoxq3PWOI0+hRD5fbF+7ayNRzwKSW3YGmaA==</PUBLICKEY><KEYDATA>lHNQkO95aAcT6qmid+sfsmXX91c=</KEYDATA></DATA><MSDRM_SIGNATURE_VALUE>nw20dAepPio7YofQbPzPsMeYwFratMUtJThV4KfmqZwqtQ1j2z4jJg==</MSDRM_SIGNATURE_VALUE><SYMSIGNATURE>VGAd8jGookzzvJyxLmPf2Gd01BA=</SYMSIGNATURE></CERTIFICATE><FALLBACK><SECURITYVERSION>2.4.104.185</SECURITYVERSION><CERTIFICATE private="1">9OBtM50oB4o3ZDzN1gBqoxq3PWOI0+hRD5fbF+7ayNRzwKSW3YGmaAIEaLlTQRdwW/QDiuDqREsaCo24vuPMUqyulUjYX2sg+q2hIrd/GdYnAqZP</CERTIFICATE></FALLBACK><CERTIFICATE type="GROUP"><DATA><NAME>Creative Zen V Plus</NAME>
  <MANUFACTURER>CL Direct Pte Ltd.</MANUFACTURER>
  <MODEL>DAP-FL0040</MODEL>
  <SECURITYLEVEL>2000</SECURITYLEVEL>
  <HARDWARE_VER_MAJOR>1</HARDWARE_VER_MAJOR>
  <HARDWARE_VER_MINOR>0</HARDWARE_VER_MINOR>
  <FIRMWARE_VER_MAJOR>1</FIRMWARE_VER_MAJOR>
  <FIRMWARE_VER_MINOR>0</FIRMWARE_VER_MINOR>
  <FEATURES>
    <CLOCK>2</CLOCK>
    <SECURECLOCK>
      <URL>http://go.microsoft.com/fwlink/?LinkId=25817</URL>
      <PUBLICKEY>!CNhvvz1WaNV1AFUmetxkvm9iD4UrE9cnGUi!qcqdxMiXmD1*ikYGA==</PUBLICKEY>
    </SECURECLOCK>
    <METERING>1</METERING>
    <LICENSE_ACQ>0</LICENSE_ACQ>
    <LICENSE_SYNC>1</LICENSE_SYNC>
    <ENCRYPTION>0</ENCRYPTION>
    <SYMMETRIC_OPT>1</SYMMETRIC_OPT>
  </FEATURES>
  <LIMITS>
    <MAXCHAINDEPTH>2</MAXCHAINDEPTH>
    <MAXLICENSESIZE>10240</MAXLICENSESIZE>
    <MAXHEADERSIZE>5120</MAXHEADERSIZE>
  </LIMITS><PUBLICKEY>SSm10tOG7n2E+lBUEwdKnZfQQEfPcuxO4YXDzx9dAwbU5nUer5vMbQ==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>cVDd1wa6+5HzUpvZb7bsqGKbiWXlKrihJW90lAYA1EUlOgz33MzwIQ==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION"><DATA><SECURITYLEVEL>2000</SECURITYLEVEL><AUTH_ID>1053</AUTH_ID><PUBLICKEY>aPD+vFB8wJZiyyqhYeYgGIxpZk29uo/JJPSgqJiTwzfeOXY+qlyrFQ==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>SywdNwotVIaw6M7gJSL73CqQcjV+ZPTHjMhFvFeHSqqRx3SRzAquJg==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION_ROOT"><DATA><AUTH_ID>1</AUTH_ID><PUBLICKEY>a1t3hxrg!qbOgktnbYaEEi4teCse!gz6RvTPuC!zizKJlpU7xoduSw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>FKndZtwHnby1q9wM50lsjE4lnQYrqctul6h7+sprWWM3UGvrVKUxEw==</MSDRM_SIGNATURE_VALUE></CERTIFICATE></DEVCERT>&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
WMPInfo.xml Does not exist on this device
PTP: Closing session
OK.


---

### Post by maddbaron on 2008-01-29
yeah I cancel when  it asks to open picture folder or upload to picture program...i clcik do nothing.

---

### Post by Magneto on 2008-01-29
hey maddbaron are you using the cvs version of libmtp?


edit**  - 

Your device is listed here [http://libmtp.sourceforge.net/index.php?page=compatibility](http://libmtp.sourceforge.net/index.php?page=compatibility) in the compatibility list but it doesn't say what version of the driver added your device. The device immediately above yours is used by the guy who made this thread [http://ubuntuforums.org/showthread.php?t=616952](http://ubuntuforums.org/showthread.php?t=616952) .

According to his correspondence with the libmtp devs his device isnt supported in the release driver so he has to use the CVS.

I'd say try the CVS first.

---

