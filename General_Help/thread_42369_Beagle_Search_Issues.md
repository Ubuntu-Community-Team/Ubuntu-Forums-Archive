---
title: "Beagle Search Issues"
date: 2005-06-17
forum: General Help
---

### Post by XDevHald on 2005-06-17
> The query for *Ubuntu* failed with error:
System.Net.Sockets.SocketException: System call failed in [0x00063] System.Net.Sockets.Socket:Connect (System.Net.EndPoint remote_end) in <0x00021> Beagle.Util.UnixClient:Connect (Mono.Posix.UnixEndPoint remoteEndPoint) in <0x00036> Beagle.Util.UnixClient:Connect (System.String path) in <0x00020> Beagle.Util.UnixClient:.ctor (System.String path) in <0x00028> Beagle.Client:SendRequest (Beagle.RequestMessage request) in <0x00010> Beagle.Client:SendAsync (Beagle.RequestMessage request) in <0x000c7> Beagle.RequestMessage:SendAsync () in <0x00142> Best.BestWindow:Search (System.String searchString)

This of course is a nasty search string, but what exactly is causing this to block to connection?

---

