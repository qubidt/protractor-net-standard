Protractor for .NET [![Build Status](https://travis-ci.org/qubidt/protractor-net-standard.svg?branch=master)](https://travis-ci.org/qubidt/protractor-net-standard)
===================

The .NET port of [Protractor](https://github.com/angular/protractor), an end to end test framework for Angular applications.

Protractor for .NET is built on top of [Selenium WebDriver](http://www.seleniumhq.org/projects/webdriver/) C# binding.

## Get it from NuGet!

    PM> Install-Package Protractor.Net.Standard

Supports Microsoft .NET Framework 4.6.1, .NET Core 2.0, Mono 5.4 and higher.

## Write tests!

```csharp
[Test]
public void ShouldGreetUsingBinding()
{
    // Instanciate a classic Selenium's WebDriver
    var driver = new ChromeDriver();
    // Configure timeouts (important since Protractor uses asynchronous client side scripts)
    driver.Manage().Timeouts().AsynchronousJavaScript = TimeSpan.FromSeconds(5);

    using (var ngDriver = new NgWebDriver(driver))
    {
        ngDriver.Url = "http://www.angularjs.org";
        ngDriver.FindElement(NgBy.Model("yourName")).SendKeys("Julie");
        Assert.AreEqual("Hello Julie!", ngDriver.FindElement(NgBy.Binding("yourName")).Text);
    }
}
```

## Getting Help

Please ask usage and debugging questions on [StackOverflow](http://stackoverflow.com/questions/tagged/protractor-net) (use the ["protractor-net"](http://stackoverflow.com/questions/ask?tags=protractor-net) tag)

## When to NOT use?

When you can use the original [Protractor](http://www.protractortest.org/) framework :)
