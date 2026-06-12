---
title: "compiling xbmc convert patch fom visual studio to linux"
date: 2012-10-19
forum: General Help
---

### Post by bilboubu on 2012-10-19
```
diff --git a/project/VS2010Express/XBMC.vcxproj b/project/VS2010Express/XBMC.vcxproj
index 4c7824d..27eadb1 100644
--- a/project/VS2010Express/XBMC.vcxproj
+++ b/project/VS2010Express/XBMC.vcxproj
@@ -839,6 +839,7 @@
     <ClCompile Include="..\..\xbmc\network\upnp\UPnPInternal.cpp" />
     <ClCompile Include="..\..\xbmc\network\upnp\UPnPRenderer.cpp" />
     <ClCompile Include="..\..\xbmc\network\upnp\UPnPServer.cpp" />
+    <ClCompile Include="..\..\xbmc\network\WakeOnAccess.cpp" />
     <ClCompile Include="..\..\xbmc\network\WebServer.cpp" />
     <ClCompile Include="..\..\xbmc\network\websocket\WebSocket.cpp" />
     <ClCompile Include="..\..\xbmc\network\websocket\WebSocketManager.cpp" />
@@ -1082,6 +1083,7 @@
     <ClInclude Include="..\..\xbmc\network\upnp\UPnPInternal.h" />
     <ClInclude Include="..\..\xbmc\network\upnp\UPnPRenderer.h" />
     <ClInclude Include="..\..\xbmc\network\upnp\UPnPServer.h" />
+    <ClInclude Include="..\..\xbmc\network\WakeOnAccess.h" />
     <ClInclude Include="..\..\xbmc\network\websocket\WebSocket.h" />
     <ClInclude Include="..\..\xbmc\network\websocket\WebSocketManager.h" />
     <ClInclude Include="..\..\xbmc\network\websocket\WebSocketV13.h" />

diff --git a/project/VS2010Express/XBMC.vcxproj.filters b/project/VS2010Express/XBMC.vcxproj.filters
index b471ebf..a6eb4d9 100644
--- a/project/VS2010Express/XBMC.vcxproj.filters
+++ b/project/VS2010Express/XBMC.vcxproj.filters
@@ -2918,6 +2918,9 @@
     <ClCompile Include="..\..\xbmc\music\tags\MusicInfoTagLoaderWav.cpp">
       <Filter>music\tags</Filter>
     </ClCompile>
+    <ClCompile Include="..\..\xbmc\network\WakeOnAccess.cpp">
+      <Filter>network</Filter>
+    </ClCompile>
     <ClCompile Include="..\..\xbmc\interfaces\python\test\TestSwig.cpp">
       <Filter>interfaces\python\test</Filter>
     </ClCompile>
@@ -5716,6 +5719,9 @@
     <ClInclude Include="..\..\xbmc\interfaces\python\XBPyThread.h">
       <Filter>interfaces\python</Filter>
     </ClInclude>
+    <ClInclude Include="..\..\xbmc\network\WakeOnAccess.h">
+      <Filter>network</Filter>
+    </ClInclude>
     <ClInclude Include="..\..\xbmc\music\tags\TagLibVFSStream.h">
       <Filter>music\tags</Filter>
     </ClInclude>
```
what should the vs2010 bit be changed to , to make it compile correctly under ubuntu?

---

