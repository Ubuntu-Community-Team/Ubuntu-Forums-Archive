---
title: "Help Building Monodevelop 0.18 from Source"
date: 2008-01-16
forum: General Help
---

### Post by GenuineXP on 2008-01-16
So I can't find an up to date package for Monodevelop and have resorted to installing from source. This required installing some other libraries from source too since packages weren't available for those either (Ubuntu's repositories tend to be stale).

I installed mono-addins-0.3, ran $ ./configure, and then $ make, but I get a native sigsegv. Here's the output.

```
$ make > make-output

** (/usr/lib/mono/2.0/gmcs.exe:14008): WARNING **: The following assembly referenced from /home/sean/Desktop/monodevelop-0.18.1/build/bin/MonoDevelop.Core.dll could not be loaded:
     Assembly:   Mono.Addins.Setup    (assemblyref_index=6)
     Version:    0.3.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/sean/Desktop/monodevelop-0.18.1/build/bin/).


** (/usr/lib/mono/2.0/gmcs.exe:14008): WARNING **: Could not load file or assembly 'Mono.Addins.Setup, Version=0.3.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

** (/usr/lib/mono/2.0/gmcs.exe:14008): WARNING **: Could not load file or assembly 'Mono.Addins.Setup, Version=0.3.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.
Stacktrace:

  at (wrapper managed-to-native) System.Reflection.MonoMethodInfo.get_method_info (intptr,System.Reflection.MonoMethodInfo&) <0x0000b>
  at (wrapper managed-to-native) System.Reflection.MonoMethodInfo.get_method_info (intptr,System.Reflection.MonoMethodInfo&) <0xffffffff>
  at System.Reflection.MonoMethod.get_Attributes () <0x0002f>
  at System.Reflection.MethodBase.get_IsVirtual () <0x00016>
  at Mono.CSharp.MemberCache.AddMethods (System.Reflection.BindingFlags,System.Type) <0x0023c>
  at Mono.CSharp.MemberCache.AddMethods (System.Type) <0x00022>
  at Mono.CSharp.MemberCache..ctor (Mono.CSharp.IMemberContainer) <0x001e4>
  at Mono.CSharp.TypeHandle..ctor (System.Type) <0x001a7>
  at Mono.CSharp.TypeHandle.GetTypeHandle (System.Type) <0x00073>
  at Mono.CSharp.TypeHandle.GetMemberCache (System.Type) <0x00012>
  at Mono.CSharp.TypeManager.MemberLookup_FindMembers (System.Type,System.Reflection.MemberTypes,System.Reflection.BindingFlags,string,bool&) <0x00308>
  at Mono.CSharp.TypeManager.RealMemberLookup (System.Type,System.Type,System.Type,System.Reflection.MemberTypes,System.Reflection.BindingFlags,string,System.Collections.IList) <0x00269>
  at Mono.CSharp.TypeManager.MemberLookup (System.Type,System.Type,System.Type,System.Reflection.MemberTypes,System.Reflection.BindingFlags,string,System.Collections.IList) <0x00047>
  at Mono.CSharp.Expression.MemberLookup (System.Type,System.Type,System.Type,string,System.Reflection.MemberTypes,System.Reflection.BindingFlags,Mono.CSharp.Location) <0x000d6>
  at Mono.CSharp.Expression.MemberLookup (System.Type,System.Type,System.Type,string,Mono.CSharp.Location) <0x00047>
  at Mono.CSharp.MemberAccess.DoResolve (Mono.CSharp.EmitContext,Mono.CSharp.Expression) <0x0045a>
  at Mono.CSharp.MemberAccess.DoResolve (Mono.CSharp.EmitContext) <0x0001d>
  at Mono.CSharp.Expression.Resolve (Mono.CSharp.EmitContext,Mono.CSharp.ResolveFlags) <0x001db>
  at Mono.CSharp.MemberAccess.DoResolve (Mono.CSharp.EmitContext,Mono.CSharp.Expression) <0x000a0>
  at Mono.CSharp.MemberAccess.DoResolve (Mono.CSharp.EmitContext) <0x0001d>
  at Mono.CSharp.Expression.Resolve (Mono.CSharp.EmitContext,Mono.CSharp.ResolveFlags) <0x001db>
  at Mono.CSharp.Invocation.DoResolve (Mono.CSharp.EmitContext) <0x000d0>
  at Mono.CSharp.Expression.Resolve (Mono.CSharp.EmitContext,Mono.CSharp.ResolveFlags) <0x001db>
  at Mono.CSharp.Expression.Resolve (Mono.CSharp.EmitContext) <0x00028>
  at Mono.CSharp.Assign.DoResolve (Mono.CSharp.EmitContext) <0x000ee>
  at Mono.CSharp.Expression.Resolve (Mono.CSharp.EmitContext,Mono.CSharp.ResolveFlags) <0x001db>
  at Mono.CSharp.Expression.Resolve (Mono.CSharp.EmitContext) <0x00028>
  at Mono.CSharp.ExpressionStatement.ResolveStatement (Mono.CSharp.EmitContext) <0x0002c>
  at Mono.CSharp.StatementExpression.Resolve (Mono.CSharp.EmitContext) <0x00037>
  at Mono.CSharp.Block.Resolve (Mono.CSharp.EmitContext) <0x00270>
  at Mono.CSharp.If.Resolve (Mono.CSharp.EmitContext) <0x002ba>
  at Mono.CSharp.Block.Resolve (Mono.CSharp.EmitContext) <0x00270>
  at Mono.CSharp.Block.Resolve (Mono.CSharp.EmitContext) <0x00270>
  at Mono.CSharp.EmitContext.ResolveTopBlock (Mono.CSharp.EmitContext,Mono.CSharp.ToplevelBlock,Mono.CSharp.Parameters,Mono.CSharp.IMethodData,bool&) <0x0020b>
  at Mono.CSharp.Constructor.Emit () <0x0037b>
  at Mono.CSharp.TypeContainer.EmitConstructors () <0x00491>
  at Mono.CSharp.TypeContainer.EmitType () <0x002c4>
  at Mono.CSharp.RootContext.EmitCode () <0x000a4>
  at Mono.CSharp.Driver.MainDriver (string[]) <0x00e6d>
  at Mono.CSharp.Driver.Main (string[]) <0x00079>
  at (wrapper runtime-invoke) System.Object.runtime_invoke_int_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

        /usr/bin/mono [0x565c2b]
        /usr/bin/mono [0x545811]
        /lib/libpthread.so.0 [0x2af6a4199100]
        /usr/bin/mono [0x48f8e8]
        [0x402abd60]

Debug info from gdb:

(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 47238811759376 (LWP 14008)]
[New Thread 1075988816 (LWP 14010)]
[New Thread 1073822032 (LWP 14009)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0x00002af6a46c13ab in fork () from /lib/libc.so.6
  3 Thread 1073822032 (LWP 14009)  0x00002af6a41987b1 in ?? ()
   from /lib/libpthread.so.0
  2 Thread 1075988816 (LWP 14010)  0x00002af6a41957a6 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  1 Thread 47238811759376 (LWP 14008)  0x00002af6a46c13ab in fork ()
   from /lib/libc.so.6

Thread 3 (Thread 1073822032 (LWP 14009)):
#0  0x00002af6a41987b1 in ?? () from /lib/libpthread.so.0
#1  0x00000000004e70aa in ?? ()
#2  0x00002af6a4191317 in start_thread () from /lib/libpthread.so.0
#3  0x00002af6a46fad5d in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 2 (Thread 1075988816 (LWP 14010)):
#0  0x00002af6a41957a6 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004ec12f in ?? ()
#2  0x00000000004ec45d in ?? ()
#3  0x00000000004ec223 in ?? ()
#4  0x00000000004fd5b0 in ?? ()
#5  0x000000000049b66d in ?? ()
#6  0x00000000004b65da in ?? ()
#7  0x00000000004fbae6 in ?? ()
#8  0x0000000000517d27 in ?? ()
#9  0x00002af6a4191317 in start_thread () from /lib/libpthread.so.0
#10 0x00002af6a46fad5d in clone () from /lib/libc.so.6
#11 0x0000000000000000 in ?? ()

Thread 1 (Thread 47238811759376 (LWP 14008)):
#0  0x00002af6a46c13ab in fork () from /lib/libc.so.6
#1  0x00002af6a3d18577 in ?? () from /usr/lib/libglib-2.0.so.0
#2  0x00002af6a3d190a4 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0x00002af6a3d19538 in g_spawn_command_line_sync ()
   from /usr/lib/libglib-2.0.so.0
#4  0x0000000000565cf4 in ?? ()
#5  0x0000000000545811 in ?? ()
#6  <signal handler called>
#7  0x000000000048f8e8 in ?? ()
#8  0x00000000402abd60 in ?? ()
#9  0x00002aaaad6d4d00 in ?? ()
#10 0x0000000000000000 in ?? ()
#0  0x00002af6a46c13ab in fork () from /lib/libc.so.6


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

/bin/bash: line 1: 14008 Aborted                 (core dumped) /usr/bin/gmcs -debug -codepage:utf8 -debug -out:../../../build/bin/MonoDevelop.Projects.dll -target:library -r:/usr/local/lib/mono/mono-addins/Mono.Addins.dll /r:/usr/lib/mono/monodoc/monodoc.dll -r:../../../build/bin/Mono.Cecil.dll -r:../../../build/bin/Mono.Cecil.Mdb.dll -r:../../../build/bin/MonoDevelop.Core.dll -r:Mono.Posix -r:System -r:System.Drawing -r:System.Xml /resource:./MonoDevelop.Projects.addin.xml ./MonoDevelop.Projects.Ambience/Ambience.cs ./MonoDevelop.Projects.Ambience/AmbienceService.cs ./MonoDevelop.Projects.Ambience/ConversionFlags.cs ./MonoDevelop.Projects.Ambience/NetAmbience.cs ./MonoDevelop.Projects.CodeGeneration/BaseRefactorer.cs ./MonoDevelop.Projects.CodeGeneration/CodeRefactorer.cs ./MonoDevelop.Projects.CodeGeneration/IRefactorer.cs ./MonoDevelop.Projects.CodeGeneration/RefactorerContext.cs ./MonoDevelop.Projects.CodeGeneration/RefactorOperations.cs ./MonoDevelop.Projects.CodeGeneration/XmlCodeDomReader.cs ./MonoDevelop.Projects.Documentation/IDocumentationService.cs ./MonoDevelop.Projects.Extensions/DataTypeCodon.cs ./MonoDevelop.Projects.Extensions/ItemPropertyCodon.cs ./MonoDevelop.Projects.Extensions/LanguageBindingCodon.cs ./MonoDevelop.Projects.Extensions/ProjectBindingCodon.cs ./MonoDevelop.Projects.Parser/AbstractDecoration.cs ./MonoDevelop.Projects.Parser/AbstractMember.cs ./MonoDevelop.Projects.Parser/AbstractNamedEntity.cs ./MonoDevelop.Projects.Parser/AbstractUsing.cs ./MonoDevelop.Projects.Parser/AssemblyCodeCompletionDatabase.cs ./MonoDevelop.Projects.Parser/AssemblyInformation.cs ./MonoDevelop.Projects.Parser/AssemblyInformationEventHandler.cs ./MonoDevelop.Projects.Parser/AttributeCollection.cs ./MonoDevelop.Projects.Parser/AttributeSectionCollection.cs ./MonoDevelop.Projects.Parser/ClassCollection.cs ./MonoDevelop.Projects.Parser/ClassEntry.cs ./MonoDevelop.Projects.Parser/ClassInformationEventHandler.cs ./MonoDevelop.Projects.Parser/ClassType.cs ./MonoDevelop.Projects.Parser/ClassWrapper.cs ./MonoDevelop.Projects.Parser/CodeCompletionDatabase.cs ./MonoDevelop.Projects.Parser/Comment.cs ./MonoDevelop.Projects.Parser/CommentCollection.cs ./MonoDevelop.Projects.Parser/CommentTasksChangedEventHandler.cs ./MonoDevelop.Projects.Parser/CompoundClass.cs ./MonoDevelop.Projects.Parser/DatabaseGeneratorTool.cs ./MonoDevelop.Projects.Parser/DefaultAttribute.cs ./MonoDevelop.Projects.Parser/DefaultClass.cs ./MonoDevelop.Projects.Parser/DefaultComment.cs ./MonoDevelop.Projects.Parser/DefaultCompilationUnit.cs ./MonoDevelop.Projects.Parser/DefaultEvent.cs ./MonoDevelop.Projects.Parser/DefaultField.cs ./MonoDevelop.Projects.Parser/DefaultIndexer.cs ./MonoDevelop.Projects.Parser/DefaultMethod.cs ./MonoDevelop.Projects.Parser/DefaultParameter.cs ./MonoDevelop.Projects.Parser/DefaultParserService.cs ./MonoDevelop.Projects.Parser/DefaultProperty.cs ./MonoDevelop.Projects.Parser/DefaultRegion.cs ./MonoDevelop.Projects.Parser/DefaultReturnType.cs ./MonoDevelop.Projects.Parser/EventCollection.cs ./MonoDevelop.Projects.Parser/ExpressionContext.cs ./MonoDevelop.Projects.Parser/FieldCollection.cs ./MonoDevelop.Projects.Parser/FileEntry.cs ./MonoDevelop.Projects.Parser/GenericParameter.cs ./MonoDevelop.Projects.Parser/GenericParameterList.cs ./MonoDevelop.Projects.Parser/IAttribute.cs ./MonoDevelop.Projects.Parser/IClass.cs ./MonoDevelop.Projects.Parser/IComment.cs ./MonoDevelop.Projects.Parser/ICompilationUnit.cs ./MonoDevelop.Projects.Parser/ICompilationUnitBase.cs ./MonoDevelop.Projects.Parser/IDecoration.cs ./MonoDevelop.Projects.Parser/IEvent.cs ./MonoDevelop.Projects.Parser/IExpressionFinder.cs ./MonoDevelop.Projects.Parser/IField.cs ./MonoDevelop.Projects.Parser/IIndexer.cs ./MonoDevelop.Projects.Parser/ILanguageItem.cs ./MonoDevelop.Projects.Parser/IMember.cs ./MonoDevelop.Projects.Parser/IMethod.cs ./MonoDevelop.Projects.Parser/IParameter.cs ./MonoDevelop.Projects.Parser/IParser.cs ./MonoDevelop.Projects.Parser/IParserService.cs ./MonoDevelop.Projects.Parser/IProperty.cs ./MonoDevelop.Projects.Parser/IRegion.cs ./MonoDevelop.Projects.Parser/IReturnType.cs ./MonoDevelop.Projects.Parser/ITypeNameResolver.cs ./MonoDevelop.Projects.Parser/IUsing.cs ./MonoDevelop.Projects.Parser/IUsingCollection.cs ./MonoDevelop.Projects.Parser/LanguageItemCollection.cs ./MonoDevelop.Projects.Parser/LocalVariable.cs ./MonoDevelop.Projects.Parser/MemberCollectionBase.cs ./MonoDevelop.Projects.Parser/MethodCollection.cs ./MonoDevelop.Projects.Parser/ModifierEnum.cs ./MonoDevelop.Projects.Parser/Namespace.cs ./MonoDevelop.Projects.Parser/NamespaceEntry.cs ./MonoDevelop.Projects.Parser/ParameterCollection.cs ./MonoDevelop.Projects.Parser/ParameterModifier.cs ./MonoDevelop.Projects.Parser/ParseInformation.cs ./MonoDevelop.Projects.Parser/ParseInformationEventHandler.cs ./MonoDevelop.Projects.Parser/PersistentAttribute.cs ./MonoDevelop.Projects.Parser/PersistentAttributeSection.cs ./MonoDevelop.Projects.Parser/PersistentClass.cs ./MonoDevelop.Projects.Parser/PersistentEvent.cs ./MonoDevelop.Projects.Parser/PersistentField.cs ./MonoDevelop.Projects.Parser/PersistentGenericParamater.cs ./MonoDevelop.Projects.Parser/PersistentIndexer.cs ./MonoDevelop.Projects.Parser/PersistentMethod.cs ./MonoDevelop.Projects.Parser/PersistentParameter.cs ./MonoDevelop.Projects.Parser/PersistentProperty.cs ./MonoDevelop.Projects.Parser/PersistentReturnType.cs ./MonoDevelop.Projects.Parser/ProjectCodeCompletionDatabase.cs ./MonoDevelop.Projects.Parser/PropertyCollection.cs ./MonoDevelop.Projects.Parser/ReferenceEntry.cs ./MonoDevelop.Projects.Parser/ReflectionClass.cs ./MonoDevelop.Projects.Parser/ReflectionEvent.cs ./MonoDevelop.Projects.Parser/ReflectionField.cs ./MonoDevelop.Projects.Parser/ReflectionIndexer.cs ./MonoDevelop.Projects.Parser/ReflectionMethod.cs ./MonoDevelop.Projects.Parser/ReflectionParameter.cs ./MonoDevelop.Projects.Parser/ReflectionProperty.cs ./MonoDevelop.Projects.Parser/ReflectionReturnType.cs ./MonoDevelop.Projects.Parser/ReturnTypeList.cs ./MonoDevelop.Projects.Parser/SimpleCodeCompletionDatabase.cs ./MonoDevelop.Projects.Parser/Tag.cs ./MonoDevelop.Projects.Parser/TagCollection.cs ./MonoDevelop.Projects.Parser/TypedCSharpCollection.cs ./MonoDevelop.Projects.Parser/TypeNameResolver.cs ./MonoDevelop.Projects.Serialization/ArrayHandler.cs ./MonoDevelop.Projects.Serialization/ArrayListHandler.cs ./MonoDevelop.Projects.Serialization/ClassDataType.cs ./MonoDevelop.Projects.Serialization/CollectionDataType.cs ./MonoDevelop.Projects.Serialization/DataCollection.cs ./MonoDevelop.Projects.Serialization/DataContext.cs ./MonoDevelop.Projects.Serialization/DataIncludeAttribute.cs ./MonoDevelop.Projects.Serialization/DataItem.cs ./MonoDevelop.Projects.Serialization/DataItemAttribute.cs ./MonoDevelop.Projects.Serialization/DataNode.cs ./MonoDevelop.Projects.Serialization/DataSerializer.cs ./MonoDevelop.Projects.Serialization/DataType.cs ./MonoDevelop.Projects.Serialization/DataValue.cs ./MonoDevelop.Projects.Serialization/EnumDataType.cs ./MonoDevelop.Projects.Serialization/ExpandedCollectionAttribute.cs ./MonoDevelop.Projects.Serialization/GenericCollectionHandler.cs ./MonoDevelop.Projects.Serialization/ICollectionHandler.cs ./MonoDevelop.Projects.Serialization/IExtendedDataItem.cs ./MonoDevelop.Projects.Serialization/ItemProperty.cs ./MonoDevelop.Projects.Serialization/ItemPropertyAttribute.cs ./MonoDevelop.Projects.Serialization/PrimitiveDataType.cs ./MonoDevelop.Projects.Serialization/SerializationContext.cs ./MonoDevelop.Projects.Serialization/XmlDataSerializer.cs ./MonoDevelop.Projects.Text/IEditableTextFile.cs ./MonoDevelop.Projects.Text/ITextFile.cs ./MonoDevelop.Projects.Text/ITextFileProvider.cs ./MonoDevelop.Projects.Text/TextEncoding.cs ./MonoDevelop.Projects.Text/TextFile.cs ./MonoDevelop.Projects.Text/TextFileReader.cs ./MonoDevelop.Projects.Text/TextFileService.cs ./MonoDevelop.Projects.Utility/DiffUtility.cs ./MonoDevelop.Projects/AbstractConfiguration.cs ./MonoDevelop.Projects/AbstractProjectConfiguration.cs ./MonoDevelop.Projects/BuildEventHandler.cs ./MonoDevelop.Projects/BuildTool.cs ./MonoDevelop.Projects/CmbxFileFormat.cs ./MonoDevelop.Projects/Combine.cs ./MonoDevelop.Projects/CombineConfiguration.cs ./MonoDevelop.Projects/CombineEntry.cs ./MonoDevelop.Projects/CombineEntryCollection.cs ./MonoDevelop.Projects/CombineEntryEventArgs.cs ./MonoDevelop.Projects/CombineEntryRenamedEventArgs.cs ./MonoDevelop.Projects/CombineEventArgs.cs ./MonoDevelop.Projects/CombineExecuteDefinition.cs ./MonoDevelop.Projects/ConfigurationCollection.cs ./MonoDevelop.Projects/ConfigurationEventHandler.cs ./MonoDevelop.Projects/ConvertXml.cs ./MonoDevelop.Projects/CustomCommand.cs ./MonoDevelop.Projects/CustomCommandCollection.cs ./MonoDevelop.Projects/CustomCommandExtension.cs ./MonoDevelop.Projects/CustomCommandType.cs ./MonoDevelop.Projects/CyclicBuildOrderException.cs ./MonoDevelop.Projects/DefaultCompilerResult.cs ./MonoDevelop.Projects/DefaultFileFormat.cs ./MonoDevelop.Projects/DotNetProject.cs ./MonoDevelop.Projects/DotNetProjectBinding.cs ./MonoDevelop.Projects/DotNetProjectConfiguration.cs ./MonoDevelop.Projects/ExecutionContext.cs ./MonoDevelop.Projects/FileFormatManager.cs ./MonoDevelop.Projects/GenericProject.cs ./MonoDevelop.Projects/GenericProjectBinding.cs ./MonoDevelop.Projects/ICompilerResult.cs ./MonoDevelop.Projects/IConfiguration.cs ./MonoDevelop.Projects/IDotNetLanguageBinding.cs ./MonoDevelop.Projects/IFileFormat.cs ./MonoDevelop.Projects/ILanguageBinding.cs ./MonoDevelop.Projects/IProjectBinding.cs ./MonoDevelop.Projects/IProjectService.cs ./MonoDevelop.Projects/LanguageBindingService.cs ./MonoDevelop.Projects/MonoDevelopFileFormat.cs ./MonoDevelop.Projects/PrjxFileFormat.cs ./MonoDevelop.Projects/Project.cs ./MonoDevelop.Projects/ProjectConvertTool.cs ./MonoDevelop.Projects/ProjectCreateInformation.cs ./MonoDevelop.Projects/ProjectEventArgs.cs ./MonoDevelop.Projects/ProjectFile.cs ./MonoDevelop.Projects/ProjectFileCollection.cs ./MonoDevelop.Projects/ProjectFileEventArgs.cs ./MonoDevelop.Projects/ProjectPathItemPropertyAttribute.cs ./MonoDevelop.Projects/ProjectReference.cs ./MonoDevelop.Projects/ProjectReferenceCollection.cs ./MonoDevelop.Projects/ProjectReferenceEventArgs.cs ./MonoDevelop.Projects/ProjectRenameEventArgs.cs ./MonoDevelop.Projects/ProjectService.cs ./MonoDevelop.Projects/ProjectServiceExtension.cs ./MonoDevelop.Projects/ProjectsServices.cs ./MonoDevelop.Projects/SharpDevelopFileFormat.cs ./MonoDevelop.Projects/UnknownCombineEntry.cs ./MonoDevelop.Projects/UnknownConfiguration.cs ./MonoDevelop.Projects/UnknownProjectVersionException.cs ./MonoDevelop.Projects/Workspace.cs AssemblyInfo.cs
make[3]: *** [../../../build/bin/MonoDevelop.Projects.dll] Error 134
make[2]: *** [all-recursive] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all-recursive] Error 1

```

Any ideas on what's going on here? Is there a way I can fix this? I'd really like to try the latest Monodevelop, but like I said, there are no packages that I can find (at least that don't claim they have dependencies that can't be resolved, including the infamous libc6).

Any help is appreciated. Thanks!

---

### Post by Deividson on 2008-01-17
i had loads of trouble installing monodevelop 0.18 on ubuntu too. i found a debian package for it, but it wont install - plus compiling from the sources seems impossible (some deps are not available, some wont compile, some wont install) - after working on it for 2 days, max i could do was installing 0.16 folowing exactly whats this howto ( [http://www.howtogeek.com/howto/linux/installing-monodevelop-from-source-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-monodevelop-from-source-on-ubuntu/) ) AFTER fresh installing ubuntu - monodevelop didnt like my install it sems.

and i tryed doing what that page says but using the 0.18 source but thats a no no too

---

### Post by .::welemski::. on 2008-02-09
Hi,

Compiling and building both mono and monodevelop has a certain build orders to follow for ti to be compiled successfully specially monodevelop 0.18.

Please follow this order for it compile flawlessly. :D


libgdiplus 1.2.6
gnome-sharp 2.16.0
gtk-sharp 2.10.2
gtkmozembed-sharp
gtksourceview2-sharp or gtksourceview-sharp
xsp 1.2.6
mono-addins 0.3
monodoc 1.2.6
monodevelop 0.18.1

-----------

---

