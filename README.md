# cordova-plugin-pgb-ios-localize-app-name

## Description

This plugin is for localizing the **App Name** ("Bundle Display Name" or CFBundleDisplayName) of **IOS PhoneGap/Cordova** applications. It does not work on other Cordova platforms (Android, Windows, etc).
It is only needed for users of **build.phonegap.com** (PhoneGap Build), because Cordova CLI users can make these changes directly in XCode.

This plugin **ONLY** localizes the name which displays under the icon when installed on the physical device. It does not localize any other content of the app.

For Example (App title translated from en "Messages" to es "Mensajes"):
![Alt text](EnglishMessagesAppIcon.png?raw=true "UI Localizations")
![Alt text](SpanishMessagesAppIcon.png?raw=true "UI Localizations")

You will want to use this plugin if you get the following iTunes Connect rejection notice:

> 3.4 - App names in iTunes Connect and as displayed on a device should be similar, so as not to cause confusion

This essentially means that you've used iTunes Connect to localize the App Name/Description that appears on the iTunes app store, but you haven't changed your compiled .ipa file to reflect the same names. This might be confusing to your users because the name which displays under the icon when used on their device will be different than the name they saw on the app store.

You can test if the localization of your app's name is working correctly by switching the language on your iOS device under "Settings / General / Language & Region / iPad Language". After switching the iPad language the device will soft-reboot. Afterwards, the text under your app's icon on the home screen should display the localized (translated) version.

## Plugin Setup

Modify your config.xml to include the following tags:
```
<!-- Note: you may omit the corresponding param tags of any language for which you do not wish to translate the app name -->
<!-- This plugin currently only supports to following languages. They were chosen to match the languages available on iTunes Connect's App Store listings. -->

	<gap:config-file platform="ios" parent="LSHasLocalizedDisplayName" mode="replace"><true/></gap:config-file>
	
	<gap:plugin platform="ios" name='cordova-plugin-pgb-ios-localize-app-name' source='npm'>
		<param name="DA_CFBUNDLEDISPLAYNAME" value="my Danish translated long name (255 character limit)" />
		<param name="DA_CFBUNDLENAME" value="my Danish translated short name (16 character limit)" />

		<param name="DE_CFBUNDLEDISPLAYNAME" value="my German translated long name (255 character limit)" />
		<param name="DE_CFBUNDLENAME" value="my German translated short name (16 character limit)" />

		<param name="EL_CFBUNDLEDISPLAYNAME" value="my Greek translated long name (255 character limit)" />
		<param name="EL_CFBUNDLENAME" value="my Greek translated short name (16 character limit)" />

		<param name="EN_CFBUNDLEDISPLAYNAME" value="my English translated long name (255 character limit)" />
		<param name="EN_CFBUNDLENAME" value="my English translated short name (16 character limit)" />

		<param name="ES_CFBUNDLEDISPLAYNAME" value="my Spanish translated long name (255 character limit)" />
		<param name="ES_CFBUNDLENAME" value="my Spanish translated short name (16 character limit)" />

		<param name="FI_CFBUNDLEDISPLAYNAME" value="my Finnish translated long name (255 character limit)" />
		<param name="FI_CFBUNDLENAME" value="my Finnish translated short name (16 character limit)" />

		<param name="FR_CFBUNDLEDISPLAYNAME" value="my French translated long name (255 character limit)" />
		<param name="FR_CFBUNDLENAME" value="my French translated short name (16 character limit)" />

		<param name="ID_CFBUNDLEDISPLAYNAME" value="my Indonesian translated long name (255 character limit)" />
		<param name="ID_CFBUNDLENAME" value="my Indonesian translated short name (16 character limit)" />

		<param name="IT_CFBUNDLEDISPLAYNAME" value="my Italian translated long name (255 character limit)" />
		<param name="IT_CFBUNDLENAME" value="my Italian translated short name (16 character limit)" />

		<param name="JA_CFBUNDLEDISPLAYNAME" value="my Japanese translated long name (255 character limit)" />
		<param name="JA_CFBUNDLENAME" value="my Japanese translated short name (16 character limit)" />

		<param name="KO_CFBUNDLEDISPLAYNAME" value="my Korean translated long name (255 character limit)" />
		<param name="KO_CFBUNDLENAME" value="my Korean translated short name (16 character limit)" />

		<param name="MS_CFBUNDLEDISPLAYNAME" value="my Malay translated long name (255 character limit)" />
		<param name="MS_CFBUNDLENAME" value="my Malay translated short name (16 character limit)" />

		<param name="NB_CFBUNDLEDISPLAYNAME" value="my Norwegian translated long name (255 character limit)" />
		<param name="NB_CFBUNDLENAME" value="my Norwegian translated short name (16 character limit)" />

		<param name="NL_CFBUNDLEDISPLAYNAME" value="my Dutch translated long name (255 character limit)" />
		<param name="NL_CFBUNDLENAME" value="my Dutch translated short name (16 character limit)" />

		<param name="PT_CFBUNDLEDISPLAYNAME" value="my Portuguese translated long name (255 character limit)" />
		<param name="PT_CFBUNDLENAME" value="my Portuguese translated short name (16 character limit)" />

		<param name="RU_CFBUNDLEDISPLAYNAME" value="my Russian translated long name (255 character limit)" />
		<param name="RU_CFBUNDLENAME" value="my Russian translated short name (16 character limit)" />

		<param name="SV_CFBUNDLEDISPLAYNAME" value="my Swedish translated long name (255 character limit)" />
		<param name="SV_CFBUNDLENAME" value="my Swedish translated short name (16 character limit)" />

		<param name="TH_CFBUNDLEDISPLAYNAME" value="my Thai translated long name (255 character limit)" />
		<param name="TH_CFBUNDLENAME" value="my Thai translated short name (16 character limit)" />

		<param name="TR_CFBUNDLEDISPLAYNAME" value="my Turkish translated long name (255 character limit)" />
		<param name="TR_CFBUNDLENAME" value="my Turkish translated short name (16 character limit)" />

		<param name="VI_CFBUNDLEDISPLAYNAME" value="my Vietnamese translated long name (255 character limit)" />
		<param name="VI_CFBUNDLENAME" value="my Vietnamese translated short name (16 character limit)" />

		<param name="ZH_CFBUNDLEDISPLAYNAME" value="my Chinese (Simplified) translated long name (255 character limit)" />
		<param name="ZH_CFBUNDLENAME" value="my Chinese (Simplified) translated short name (16 character limit)" />

		<param name="ZH_HANT_CFBUNDLEDISPLAYNAME" value="my Chinese (Traditional) translated long name (255 character limit)" />
		<param name="ZH_HANT_CFBUNDLENAME" value="my Chinese (Traditional) translated short name (16 character limit)" />
	</gap:plugin>
```

## Behind-The-Scenes Tour

For anyone who is curious how this works behind the scenes (or if you're a Cordova CLI user wanting to do this directly in XCode)

The app's main Info.plist (binary XML file) needs the "Application has localized display name" LSHasLocalizedDisplayName setting set to "Yes" ( `<true/>` in XML )
If you want to view your Info.plist file in a normal text editor you can use the plutil executable (in iTunes install directory) to decode from binary xml to xml.

Your .ipa file also needs a set of files titled [languagecode].lproj/InfoPlist.strings next to the www folder (not inside it). These files need to specify values for the CFBundleDisplayName & CFBundleName variables.
For example, if you unzip your .ipa file, you should see the following (assuming english & spanish localized app name):
```
	[MyAppName].ipa\
		Payload\
			[MyAppName].app\
				en.lproj\
					InfoPlist.strings
				es.lproj\
					InfoPlist.strings
				...
				config.xml
				Info.plist
				www\
					index.html
					cordova.js
				...

```

The contents of the [MyAppName].ipa\Payload\[MyAppName].app\en.lproj\InfoPlist.strings should be:
```
	CFBundleDisplayName = "My English Translated Long App Name";
	CFBundleName = "My English Translated Short App Name";
```
	
Note: It is not document if/where the CFBundleName is actually used, but it is still considered best practice to give it a localized value.

Note: The iTunes App Store description lists which localizations are available for the actual UI **inside** your app.
![Alt text](UILocalizationScreenShot.png?raw=true "UI Localizations")
If you desire to modify the languages listed on the above iTunes App Store screenshot, you may use the following code in your config.xml
```
	<gap:config-file platform="ios" parent="CFBundleLocalizations" mode="replace">
		<array>
			<string>da</string> <!-- danish -->
			<string>de</string> <!-- german -->
			<string>el</string> <!-- greek -->
			<string>en</string> <!-- english -->
			<string>es</string> <!-- spanish -->
			<string>fi</string> <!-- finnish -->
			<string>fr</string> <!-- french -->
			<string>id</string> <!-- indonesian -->
			<string>it</string> <!-- italian -->
			<string>ja</string> <!-- japanese -->
			<string>ko</string> <!-- korean -->
			<string>ms</string> <!-- malay -->
			<string>nb</string> <!-- norwegian -->
			<string>nl</string> <!-- dutch -->
			<string>pt</string>  <!-- portuguese -->
			<string>ru</string> <!-- russian -->
			<string>sv</string> <!-- swedish -->
			<string>th</string> <!-- thai -->
			<string>tr</string> <!-- turkish -->
			<string>vi</string> <!-- vietnamese -->
			<string>zh</string> <!-- chinese (simplified) -->
			<string>zh-hant</string>  <!-- chinese (traditional) -->
		</array>
	</gap:config-file>
```
Note: These config.xml tags don't require the use this or any other plugin. However, **ALL** they do is specify to the user which languages are available **inside** the app's UI. The tags don't magically translate anything. It is up to the programmer to write the code which actually detects the user's region & dynamically modifies the text in the html/css/js of his application. There may be some other Cordova plugins or javascript libraries that can help with this.
These tags are not required if you only want to translate your app's icon title to match your iTunes Connect App Store listing.

## Contributing

Pull requests are welcome! :)

## License

```
The MIT License (MIT)

Copyright (c) 2015 Devin Garner

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```