# [![ScalaWebTest](http://www.scalawebtest.org/images/swt-logo-light.png)](http://www.scalawebtest.org)
###### [![Build Status](https://travis-ci.org/unic/ScalaWebTest.svg?branch=master)](https://travis-ci.org/unic/ScalaWebTest)
ScalaWebTest is a library for writing ScalaTest/Selenium based integration tests for websites. It helps you with your basic setup and provides a new and very efficient approach to testing.

In manufacturing it is common to use gauges (also called checking gauges or testing gauges) to verify whether a workpiece meets predefined criteria and tolerances. ScalaWebTest transfers this concept to the world of web integration testing. You can define a gauge in HTML, and use it to verify your web application. This greatly improves the readability, simplicity of your integration tests.

Read the full documentation on our website http://www.scalawebtest.org

## How to Release

### Prerequisites
Create the following file ~/.sbt/0.13/plugins/gpg.sbt

Add the following line to gpg.sbt
`addSbtPlugin("com.jsuereth" % "sbt-pgp" % "1.0.0")`

Copy the private key (Sonatype PGP Private and Public Key from our company password store), to ~/.sbt/gpg/secring.ast

### Release
The release process of ScalaWebTest is currently done manually. The process is done as follows:

1. Switch the version in `build.sbt` to that which is to be released (e.g. from `0.0.1-SNAPSHOT` to `1.0.0`)
1. Commit your changes with the commit message "Release x.x.x" (e.g. `Release 1.0.0`)
1. Tag this commit with the release version
1. Push you changes and the tag
1. In your command line type in the following:
	1. the long way:
		1. `sbt` - enters the sbt interactive mode
		r. `+ clean` - deletes all generated files (target)
		1. `+ compile` - compiles the main sources
		1. `+ inttest` - compiles and run the integration tests
		1. `+ publishSigned` - creates all of the below plus the poms
		1. Enter the Sonatype PGP Key Password as stored in our company password store
		1. Go to https://oss.sonatype.org/#stagingRepositories verify and close the staging repository
		1. `exit` - exits the sbt interactive mode
1. Switch the version in `build.sbt` to the snapshot version (e.g. from `1.0.0` to `1.0.0-SNAPSHOT`) and update the documentation if needed
1. Finally commit those changes with the commit message "Release x.x.x complete" (e.g. `Release 1.0.0 complete`)