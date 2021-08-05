# Tech.Productivity: OpenConnect, A Fantastic AnyConnect Alternative

## Are you satisfied with AnyConnect ?

Since you are reading this article, I assume you are using AnyConnect either for your school or work. And from the feedback of myself and friends, I will put my money on that you don’t like it either. Here are a few very common complaints (on Mac) I gathered over the years and I bet, at least, you have some of them, too.

* VPN sometimes crashes severely which blocks the whole internet with it. One has to restart to solve the issue.

* VPN connection becomes unstable after a few hours of use, which makes the remote meeting very frustrating.

* VPN session is too short. You want to stay in the VPN longer without reconnecting.

* VPN client does not support split tunneling, which means no airdrop, no AirPods auto-switch, no synergy...

Admittedly, problems can be on the client-side or on the server-side. Sometimes, an inconvenience from the user side is a security policy mandated by the admins. We all understand that I hope.

But, from my personal experience, all the above problems went away when I changed the VPN client from AnyConnect to OpenConnect, which is a powerful sign that, in my case, all the above limitations arise from a bad client.

## What is OpenConnect ?

OpenConnect is a well-known cross-platform [open-source project](https://www.infradead.org/openconnect/index.html) and it is in the Ubuntu `universe` [repository](https://packages.ubuntu.com/hirsute/openconnect). It is an open-sourced version of AnyConnect but with more protocols and extended functionality.

At its core, OpenConnect is a command-line VPN client. But there are many projects built around OpenConnect and expand its usability. For example, [openconnect-gui](https://gitlab.com/openconnect/openconnect-gui) provides a cross-platform GUI interface; [ocserv](https://gitlab.com/openconnect/ocserv/) provides an open-source Linux SSL VPN server; [openconnect-sso](https://github.com/vlaci/openconnect-sso) provides support for Azure AD (SAMLv2) authentication to Cisco SSL-VPNs.

With those tools, OpenConnect becomes a competitive alternative for the AnyConnect, which solved all my problems with AnyConnect. Now I can enjoy longer and stabler VPN sessions without reconnections or crashes. I have no connection problem when video calling my colleagues in another country. And airdrop just works.

## How can I install and use OpenConnect ?

I encourage readers to explore more help from tech forums such as [stackoverflow](https://stackoverflow.com/questions/tagged/openconnect), while this article can cover the very basics of usage of OpenConnect. There are simply too many VPN configs you can play with to cover and too few free VPN services a single writer has to test against.

## Installation 

To install OpenConnect is easy.

For Windows, you can just [download](https://github.com/openconnect/openconnect-gui/releases) from the official GitHub release page.

On Linux or Mac, open a terminal or powershell, then follow the steps below:

	# Installing openconnect core
	# On Unbuntu:
	apt install openconnect
	# On Mac:
	brew install openconnect

If you are already using AnyConnect, it seems ``openconnect-sso`` can automatically pick up your AnyConnect VPN servers. Installation follows:

	# On Ubuntu or Mac
	pip install --user openconnect-sso
	# The official guide recommends installation using pipx, please check:
	# https://github.com/vlaci/openconnect-sso

If you would like a graphical interface as the Windows client does, you can download an extension:

	#On Ubuntu:
	apt install network-manager-openconnect
	# On mac:
	brew install --cask openconnect-gui

## Usage

Normally, you would just use OpenConnect like AnyConnect, especially when you have GUI installed. If you are on the command line, here is an example:

	openconnect http://YourVpnServer.com

## What about Two-Factor Authentication ?

OpenConnect supports TFA surprisingly well. With TFA, they will ask you to input a password twice where the first password is NOT your password but your preferred way of authentication instead. Please check [here](https://dmoerner.wordpress.com/2015/11/04/howto-openconnect-vpn-with-duo-multifactor-authentication/) for details. 

Had the above method failed you. You must try ``openconnect-sso`` from the command line:

	# On Mac or Ubuntu
	openconnect-sso

<span style="font-family:Papyrus; font-size:10em;">Enjoy!</span>