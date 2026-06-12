---
title: "Hydrogen crashes"
date: 2006-12-20
forum: General Help
---

### Post by Tehut on 2006-12-20
Log:
[WARNING]   JackDriver          [setBpm] 120
[WARNING]   JackDriver          calling jack_transport_locate(0)
[WARNING]   JackDriver          calling jack_transport_locate(0)
[WARNING]   JackDriver          [updateTransportInfo] internal frames != jack tr
ansport frames. resync!
[WARNING]   JackDriver          calling jack_transport_locate(0)
[WARNING]   JackDriver          [updateTransportInfo] internal frames != jack tr
ansport frames. resync!
[WARNING]   JackDriver          calling jack_transport_locate(0)
[WARNING]   JackDriver          [updateTransportInfo] internal frames != jack tr
ansport frames. resync!
[WARNING]   JackDriver          calling jack_transport_locate(0)
[WARNING]   JackDriver          [updateTransportInfo] internal frames != jack tr
ansport frames. resync!
[WARNING]   JackDriver          calling jack_transport_locate(0)
[WARNING]   JackDriver          [updateTransportInfo] internal frames != jack tr
ansport frames. resync!
[WARNING]   JackDriver          calling jack_transport_locate(0)
[WARNING]   JackDriver          [updateTransportInfo] internal frames != jack tr
ansport frames. resync!
[WARNING]   JackDriver          calling jack_transport_locate(0)
[WARNING]   JackDriver          [updateTransportInfo] internal frames != jack tr
ansport frames. resync!
[WARNING]   JackDriver          calling jack_transport_locate(0)
[WARNING]   JackDriver          [updateTransportInfo] internal frames != jack tr
ansport frames. resync!
[WARNING]   JackDriver          calling jack_transport_locate(0)
[WARNING]   JackDriver          [updateTransportInfo] internal frames != jack tr
ansport frames. resync!
[WARNING]   JackDriver          calling jack_transport_locate(0)
[WARNING]   JackDriver          [updateTransportInfo] internal frames != jack tr                     ansport frames. resync!
[WARNING]   JackDriver          calling jack_transport_locate(0)
[WARNING]   JackDriver          [updateTransportInfo] internal frames != jack tr                     ansport frames. resync!
[WARNING]   JackDriver          calling jack_transport_locate(0)
[WARNING]   JackDriver          [updateTransportInfo] internal frames != jack tr                     ansport frames. resync!
[WARNING]   JackDriver          calling jack_transport_locate(0)
[WARNING]   JackDriver          [updateTransportInfo] internal frames != jack tr                     ansport frames. resync!
[WARNING]   JackDriver          calling jack_transport_locate(0)
[WARNING]   JackDriver          [updateTransportInfo] internal frames != jack tr                     ansport frames. resync!
[WARNING]   Hydrogen            [audioEngine_process] trylock != 0. Frames = 0.                      Lock in PatternEditor::mousePressEvent
[WARNING]   Hydrogen            [audioEngine_process] trylock != 0. Frames = 0.                      Lock in PatternEditor::mousePressEvent
terminate called after throwing an instance of 'St9bad_alloc'
  what():  St9bad_alloc

Anyone got any ideas regarding the source of that error?

---

### Post by Tehut on 2006-12-21
bump

---

### Post by Tehut on 2006-12-21
bump

---

### Post by christhemonkey on 2006-12-21
Can you give more information?

Are you running a jack server already?
Are you trying to sync hydrogens transport with jack's?
Is there a transport master already running? (eg ardour)

---

