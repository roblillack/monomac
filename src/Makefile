#
# Figure out if I want to use [New] or remove from contract
#
WARNINGS_I_SHOULD_FIX=114,108

MACCORE_DIR ?= ../../maccore

#
# CORE_SOURCES are source files that are written by hand
# and are linked with the generator
#

CORE_SOURCES =					\
	Constants.cs					\
	./AppKit/Enums.cs				\
	./AppKit/Defs.cs				\
	./Foundation/EnumDesktop.cs			\
	./Foundation/NSObject.cs			\
	./ImageKit/Enums.cs				\
	./ObjCRuntime/Class.cs				\
	./ObjCRuntime/Messaging.cs			\
	./ObjCRuntime/NativeConstructorBuilder.cs	\
	./ObjCRuntime/NativeImplementationBuilder.cs	\
	./ObjCRuntime/NativeMethodBuilder.cs		\
	./ObjCRuntime/MethodDescription.cs		\
	./ObjCRuntime/NSObjectMarshaler.cs		\
	./ObjCRuntime/SelectorMarshaler.cs		\
	./ObjCRuntime/Runtime.cs			\
	./ObjCRuntime/RequiredFrameworkAttribute.cs	\
	./ObjCRuntime/Selector.cs			\
	./PdfKit/Enums.cs				\
	./QTKit/Defs.cs					\
	./QTKit/Enums.cs				\
	./OpenGL/CGLEnums.cs				\
	./OpenGL/CGLContext.cs				\
	./OpenGL/CGLPixelFormat.cs			\
	./ScriptingBridge/Enums.cs			\
	./WebKit/Enums.cs

# Sources that are not part of CORE_SOURCES or the generated templates
MONOMAC_SOURCES = \
	./Foundation/NSObjectMac.cs			\
	./Foundation/NSSearchPath.cs		\
	./AppKit/AppKitSynchronizationContext.cs	\
	./AppKit/ActionDispatcher.cs			\
	./AppKit/BeginSheet.cs				\
	./AppKit/DoubleWrapper.cs			\
	./AppKit/Functions.cs				\
	./AppKit/NSActionCell.cs			\
	./AppKit/NSApplication.cs			\
	./AppKit/NSApplicationDelegate.cs		\
	./AppKit/NSBitmapImageRep.cs			\
	./AppKit/NSButton.cs				\
	./AppKit/NSBezierPath.cs			\
	./AppKit/NSColor.cs				\
	./AppKit/NSControl.cs				\
	./AppKit/NSGradient.cs				\
	./AppKit/NSGraphics.cs				\
	./AppKit/NSImage.cs				\
	./AppKit/NSLevelIndicator.cs			\
	./AppKit/NSMatrix.cs				\
	./AppKit/NSMenu.cs				\
	./AppKit/NSMenuItem.cs				\
	./AppKit/NSOpenGLContext.cs			\
	./AppKit/NSOpenGLPixelFormat.cs			\
	./AppKit/NSPopUpButton.cs			\
	./AppKit/NSPopUpButtonCell.cs			\
	./AppKit/NSSegmentedControl.cs			\
	./AppKit/NSTableView.cs				\
	./AppKit/NSWindow.cs				\
	./CoreVideo/CVDisplayLink.cs			\
	./Growl/Constants.cs				\
	./QTKit/QTCaptureDevice.cs			\
	./QTKit/QTMovie.cs				\
	./WebKit/DomNode.cs				\
	./WebKit/Enumerators.cs				\
	./WebKit/Indexers.cs				\
	./WebKit/WebKit.cs				\
	./WebKit/WebView.cs				\
	./OpenGL/FrameEventArgs.cs			\
	./OpenGL/IGameWindow.cs				\
	./OpenGL/INativeWindow.cs			\
	./OpenGL/WindowBorder.cs			\
	./OpenGL/WindowState.cs				\
	./OpenGL/MonoMacGameView.cs			\
	./Security/Authorization.cs

OPENTK_SOURCES = \
	./OpenGL/OpenTK/Graphics/Color4.cs		\
	./OpenGL/OpenTK/Graphics/OpenGL/GL.cs		\
	./OpenGL/OpenTK/Graphics/OpenGL/GLCore.cs	\
	./OpenGL/OpenTK/Graphics/OpenGL/GLEnums.cs	\
	./OpenGL/OpenTK/Graphics/OpenGL/GLHelper.cs	\
	./OpenGL/OpenTK/Audio/ContextHandle.cs	\
	./OpenGL/OpenTK/Audio/OpenAL/AL/ALEnums.cs	\
	./OpenGL/OpenTK/Audio/BlittableValueType.cs	\
	./OpenGL/OpenTK/Audio/OpenAL/AL/AL.cs	\
	./OpenGL/OpenTK/Audio/OpenAL/Alc/AlcEnums.cs	\
	./OpenGL/OpenTK/Audio/OpenAL/Alc/Alc.cs	\
	./OpenGL/OpenTK/Math/Half.cs			\
	./OpenGL/OpenTK/Math/MathHelper.cs		\
	./OpenGL/OpenTK/Math/Matrix3d.cs		\
	./OpenGL/OpenTK/Math/Matrix4.cs			\
	./OpenGL/OpenTK/Math/Matrix4d.cs		\
	./OpenGL/OpenTK/Math/Quaternion.cs		\
	./OpenGL/OpenTK/Math/Quaterniond.cs		\
	./OpenGL/OpenTK/Math/Vector2.cs			\
	./OpenGL/OpenTK/Math/Vector2d.cs		\
	./OpenGL/OpenTK/Math/Vector2h.cs		\
	./OpenGL/OpenTK/Math/Vector3.cs			\
	./OpenGL/OpenTK/Math/Vector3d.cs		\
	./OpenGL/OpenTK/Math/Vector3h.cs		\
	./OpenGL/OpenTK/Math/Vector4.cs			\
	./OpenGL/OpenTK/Math/Vector4d.cs		\
	./OpenGL/OpenTK/Math/Vector4h.cs

GENERATOR_SOURCES = \
	$(MACCORE_DIR)/src/generator.cs			\
	$(MACCORE_DIR)/src/Options.cs			\
	$(MACCORE_DIR)/src/btouch.cs

SOURCES = \
	$(CORE_SOURCES)

DEFINES = -define:NET_2_0

TARGETS = _bmac.exe MonoMac.dll  parse.exe bmac.exe

include Make.shared

SHARED_API = \
	./avfoundation.cs	\
	./foundation.cs		\
	./coreanimation.cs	\
	./coredata.cs		\
	./coreimage.cs		\
	./coremidi.cs		\
	./corelocation.cs	\
	./quicklook.cs

SHARED_SOURCES = $(patsubst %,$(MACCORE_DIR)/src/%,$(SHARED_SOURCE))
SHARED_CORE_SOURCES = $(patsubst %,$(MACCORE_DIR)/src/%,$(SHARED_CORE_SOURCE))
SHARED_APIS = $(patsubst %,$(MACCORE_DIR)/src/%,$(SHARED_API))

APIS = \
	appkit.cs		\
	corewlan.cs		\
	foundation-desktop.cs 	\
	growl.cs		\
	imagekit.cs		\
	qtkit.cs		\
	pdfkit.cs		\
	webkit.cs		\
	composer.cs		\
	scriptingbridge.cs		\
	$(SHARED_APIS)

all: $(TARGETS)

parse.exe: parse.cs $(MACCORE_DIR)/src/Options.cs
	gmcs parse.cs $(MACCORE_DIR)/src/Options.cs

core.dll: $(CORE_SOURCES) $(SHARED_CORE_SOURCES) Makefile
	gmcs -target:library -debug -unsafe -out:core.dll -define:MONOMAC,MONOMAC_BOOTSTRAP,COREBUILD $(CORE_SOURCES) $(SHARED_CORE_SOURCES) -r:System.Drawing

_bmac.exe: $(APIS) core.dll $(GENERATOR_SOURCES)
	gmcs -unsafe -out:_bmac.exe -debug $(DEFINES) -define:GENERATOR,MONOMAC,MONOMAC_BOOTSTRAP $(GENERATOR_SOURCES) -r:core.dll -r:System.Drawing

generated_sources: _bmac.exe $(APIS) 
	mono --debug _bmac.exe -a -d=MONOMAC --core --sourceonly=generated_sources -v -tmpdir=. $(APIS) --baselib=core.dll --ns=MonoMac.ObjCRuntime -r=System.Drawing

bmac.exe: MonoMac.dll $(GENERATOR_SOURCES)
	gmcs -unsafe -out:bmac.exe -debug $(DEFINES) -define:GENERATOR,MONOMAC,MONOMAC_BOOTSTRAP $(GENERATOR_SOURCES) -r:MonoMac.dll -r:System.Drawing

count: 
	make pass | wc -l

counts:
	make pass | grep 'could not be' | sed 's/.*`//' | sed "s/'.*//" | sort | uniq -c | sort -n

MonoMac.dll: $(SOURCES) generated_sources $(MONOMAC_SOURCES) $(SHARED_SOURCES) $(SHARED_CORE_SOURCES) $(OPENTK_SOURCES)
	gmcs -define:OBJECT_REF_TRACKING -nowarn:3021,0219,0414,$(WARNINGS_I_SHOULD_FIX) -debug -unsafe $(SOURCES) @generated_sources $(MONOMAC_SOURCES) $(SHARED_SOURCES) $(SHARED_CORE_SOURCES) $(OPENTK_SOURCES) -target:library -define:MONOMAC -out:MonoMac.dll -r:System.Drawing

clean:
	rm -f $(TARGETS) core.dll

all: MonoMac.dll

update: MonoMac.dll
	cp MonoMac.dll* /Applications/MonoDevelop.app/Contents/MacOS/lib/monodevelop/Addins
	cp MonoMac.dll* /Applications/MonoDevelop.app/Contents/MacOS/lib/monodevelop/Addins/MonoDevelop.MonoMac

#
# Pushes this to the MonoDevelop source code repo
#
push-to-monodevelop: MonoMac.dll
	cp MonoMac.dll* /cvs/md/monodevelop/extras/MonoDevelop.MonoMac/MonoDevelop.MonoMac

#
# Pushes the assembly to the system MonoDevelop, for testing
#
upgrade-monodevelop: MonoMac.dll
	cp MonoMac.dll* /Applications/MonoDevelop.app/Contents/MacOS//lib/monodevelop/AddIns/MonoDevelop.MonoMac/
