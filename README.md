# AR Face Filters

> ⚠️ **Note:** This project is no longer actively maintained. It is provided as-is for reference and educational purposes.

A Unity-based Augmented Reality (AR) application that allows users to apply real-time face filters and effects using ARKit/ARCore technology. Browse a catalog of face filters organized by categories and subcategories, then preview them in real-time on a user's face.

## Features

- 🎭 **Real-time Face Detection & Rendering** - Uses ARFoundation for cross-platform AR support (iOS/Android)
- 📦 **Product Catalog System** - Organized filter catalog with categories and subcategories
- 🎯 **Filter Browsing UI** - Intuitive interface to browse and select face filters
- 🔍 **Advanced Filtering** - Filter products by categories and subcategories with toggle controls
- ⚡ **Performance Optimized** - XR subsystem management for optimal battery and performance
- 🎨 **Customizable Product Database** - JSON-based product catalog for easy updates

## Project Structure

```
Assets/Scripts/
├── ProductManager.cs          # Manages product catalog loading from JSON
├── UIController.cs            # Main UI controller for panels and filter interactions
├── Product.cs                 # Data models and catalog extensions
├── CategoryUI.cs              # UI component for product categories
├── SubCategoryUI.cs           # UI component for product subcategories
└── ProductButtonUI.cs         # Individual product button UI component
```

## Core Components

### ProductManager
Responsible for loading and managing the product catalog from a JSON asset. Provides singleton-like access to the product catalog throughout the application.

**Key Methods:**
- `FetchProducts()` - Deserializes JSON product data using Unity's JsonUtility
- `Catalog` - Property that provides access to the loaded product catalog

### UIController
Main controller orchestrating the entire UI flow and AR experience. Manages switching between the shopping catalog and AR filter preview modes.

**Key Features:**
- Dynamic UI generation from product catalog
- Panel animations (shopping catalog vs. filters panel)
- AR session lifecycle management (start/stop XR subsystems)
- Filter application and reset functionality
- Category and subcategory filtering

**Key Methods:**
- `CreateUI()` - Instantiates product buttons and category filters
- `ClickShowPanelShoppingCatalog(bool)` - Toggle between catalog and AR preview
- `ClickTogglePanelFilters()` - Show/hide filter panel
- `ClickFiltersApply()` - Apply selected category/subcategory filters
- `ClickFiltersReset()` - Clear all filter selections

### Product Data Models
Serializable data structures for product information:

- **ProductCatalog** - Container for all products
- **Product** - Individual product with name, category, subcategory, and prefab path
- **ProductRuntime** - Runtime data structures for category/subcategory state
- **Extension Methods** - Utility methods to extract categories and subcategories from catalog

### Category & SubCategory UI
Hierarchical UI components that manage filter selections:

- **CategoryUI** - Represents a category with collapsible subcategories
- **SubCategoryUI** - Individual toggle for filtering by subcategory

### ProductButtonUI
UI component for individual product selection buttons displaying product name and categorization.

## Requirements

- **Unity 2019.4+** (recommended: 2020 LTS or later)
- **ARFoundation** (XR Plug-in Management)
- **TextMesh Pro** (included with modern Unity versions)
- **iOS 13+** or **Android 7.0+** with ARCore/ARKit support
- **Platform Specific:**
  - iOS: ARKit support
  - Android: Google Play Services for AR (ARCore)

## Getting Started

### 1. Setup
- Open the project in Unity
- Ensure AR Foundation and XR Plug-in Management packages are installed
- Configure platform-specific settings in Project Settings > XR Plug-in Management

### 2. Product Catalog Configuration
Create or modify the product catalog JSON file with the following structure:

```json
{
  "products": [
    {
      "productName": "Filter Name",
      "category": "Category Name",
      "subCategory": "SubCategory Name",
      "prefab": "Prefabs/Path/To/YourFilter"
    }
  ]
}
```

### 3. Building & Deployment
- **iOS:** Switch platform to iOS, configure signing, and build
- **Android:** Switch platform to Android, configure build settings, and build APK/AAB

## Usage

1. **Browse Filters** - Open the shopping catalog to view available filters
2. **Select Filter** - Tap a filter to apply it to the camera feed
3. **Filter Results** - Use the filter panel to show/hide specific categories
4. **Reset Filters** - Clear all selections to show all products

## Architecture Notes

### UI Generation Pattern
The `UIController` dynamically generates UI elements from the product catalog at runtime, ensuring that the interface stays synchronized with the catalog data without manual hierarchy setup.

### XR Subsystem Management
The app intelligently manages AR subsystems:
- **Stops subsystems** when browsing the catalog (saves battery)
- **Starts subsystems** when entering AR preview mode
- **Disables AR components** when not in use

### Performance Considerations
- Frame rate is capped during catalog browsing to reduce power consumption
- AR session is disabled when not actively previewing filters
- Prefabs are dynamically loaded from Resources folder on demand

## Dependencies

- **Unity Engine** - Core game engine
- **ARFoundation** - Cross-platform AR support
- **XR Plug-in Management** - XR subsystem management
- **TextMesh Pro** - UI text rendering
- **Animator** - Panel and subcategory animations

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.

## Contributing

Contributions are welcome! Feel free to submit issues and pull requests to improve the project.

## Future Enhancements

- [ ] Real-time filter preview in catalog without AR
- [ ] Filter favorites/bookmarking system
- [ ] User-generated content support
- [ ] Filter ratings and reviews
- [ ] Custom filter creation tools
- [ ] Cross-device cloud sync
- [ ] Advanced face detection (expressions, landmarks)
- [ ] Video recording with filters

## Support

For issues, questions, or feature requests, please open an issue on the GitHub repository.

---

**Author:** reekdeb  
**Last Updated:** 2026
