# ASP.NET Core Localization Demo

This project demonstrates how to implement localization in an ASP.NET Core MVC application, supporting multiple languages and cultures.

## Features

- Multi-language support (English and German)
- View-based localization using `IViewLocalizer`
- Culture-based content rendering
- Default culture setting (German)
- Resource-based localization

## Prerequisites

- .NET 6.0 SDK or later
- Visual Studio 2022 or any preferred IDE

## Project Structure

```
Localization/
├── Resources/
│   └── Views/          # Contains view-specific resource files
├── Views/
│   └── Home/
│       └── Index.cshtml # Example view with localization
└── Program.cs          # Configuration for localization
```

## Setup and Configuration

The project is configured with the following localization settings:

1. Supported cultures:
   - English (en-US)
   - German (de-DE)

2. Default culture is set to German (de-DE)

3. Resource files are stored in the `Resources` directory

## How It Works

### Basic Configuration

The localization is configured in `Program.cs`:

```csharp
builder.Services.AddLocalization(options => options.ResourcesPath = "Resources");

builder.Services.Configure<RequestLocalizationOptions>(options =>
{
    var supportedCultures = new[] { "en-US", "de-DE" };
    options.SetDefaultCulture(supportedCultures[1]);
    options.SupportedCultures = supportedCultures.Select(c => new CultureInfo(c)).ToList();
    options.SupportedUICultures = options.SupportedCultures;
});
```

### View Localization

Views use the `IViewLocalizer` service for localization:

```csharp
@using Microsoft.AspNetCore.Mvc.Localization
@inject IViewLocalizer Localizer

<h1>@Localizer["Welcome"]</h1>
```

## Adding New Languages

To add a new language:

1. Create new resource files in the `Resources` directory
2. Add the culture code to the supported cultures list in `Program.cs`
3. Create corresponding resource files for views

## Contributing

Feel free to submit issues and enhancement requests.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
