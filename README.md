# nimp-web-app
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nutrient and Irrigation Management Plan (NIMP)</title>
    <style>
        :root {
            --primary-color: #1a73e8;
            --secondary-color: #5f6368;
            --accent-color: #188038;
            --light-grey: #f8f9fa;
            --border-color: #dadce0;
            --error-color: #d93025;
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
        }
        
        body {
            background-color: #f5f5f5;
            color: #333;
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            background-color: var(--primary-color);
            color: white;
            padding: 20px 0;
            text-align: center;
            margin-bottom: 30px;
        }
        
        h1 {
            font-size: 2.2rem;
            margin-bottom: 10px;
        }
        
        h2 {
            font-size: 1.8rem;
            margin: 30px 0 15px;
            color: var(--primary-color);
        }
        
        h3 {
            font-size: 1.4rem;
            margin: 20px 0 10px;
            color: var(--secondary-color);
        }
        
        .card {
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            padding: 20px;
            margin-bottom: 30px;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
        }
        
        input, select, textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            font-size: 16px;
        }
        
        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 0 2px rgba(26, 115, 232, 0.2);
        }
        
        .btn {
            display: inline-block;
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            transition: background-color 0.3s;
        }
        
        .btn:hover {
            background-color: #0d62d0;
        }
        
        .btn-secondary {
            background-color: var(--secondary-color);
        }
        
        .btn-secondary:hover {
            background-color: #4a4e52;
        }
        
        .btn-accent {
            background-color: var(--accent-color);
        }
        
        .btn-accent:hover {
            background-color: #0f6429;
        }
        
        .form-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            grid-gap: 20px;
        }
        
        .result-section {
            margin-top: 30px;
            display: none;
        }
        
        .result-section h3 {
            border-bottom: 2px solid var(--primary-color);
            padding-bottom: 5px;
            margin-bottom: 15px;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 20px;
        }
        
        table, th, td {
            border: 1px solid var(--border-color);
        }
        
        th, td {
            padding: 12px;
            text-align: left;
        }
        
        th {
            background-color: var(--light-grey);
            font-weight: bold;
        }
        
        tr:nth-child(even) {
            background-color: var(--light-grey);
        }
        
        .chart-container {
            height: 400px;
            margin: 20px 0;
        }
        
        .alert {
            padding: 15px;
            margin-bottom: 20px;
            border-radius: 4px;
        }
        
        .alert-success {
            background-color: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
        }
        
        .alert-danger {
            background-color: #f8d7da;
            color: var(--error-color);
            border: 1px solid #f5c6cb;
        }
        
        .tab-container {
            margin-bottom: 30px;
        }
        
        .tab-buttons {
            display: flex;
            border-bottom: 1px solid var(--border-color);
            margin-bottom: 20px;
        }
        
        .tab-button {
            padding: 10px 20px;
            background-color: transparent;
            border: none;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s;
        }
        
        .tab-button.active {
            color: var(--primary-color);
            border-bottom: 3px solid var(--primary-color);
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        footer {
            text-align: center;
            padding: 20px 0;
            margin-top: 50px;
            background-color: var(--light-grey);
            border-top: 1px solid var(--border-color);
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <h1>Nutrient and Irrigation Management Plan (NIMP)</h1>
            <p>Environmental Engineering Innovations</p>
        </div>
    </header>

    <div class="container">
        <div class="card">
            <h2>Welcome to the NIMP Web Application</h2>
            <p>This tool helps you calculate nutrient and irrigation requirements based on environmental factors. Please navigate through the tabs to enter your data and generate your management plan.</p>
        </div>

        <div class="tab-container">
            <div class="tab-buttons">
                <button class="tab-button active" data-tab="site-info">Site Information</button>
                <button class="tab-button" data-tab="soil-data">Soil Data</button>
                <button class="tab-button" data-tab="plant-data">Plant Data</button>
                <button class="tab-button" data-tab="water-balance">Water Balance</button>
                <button class="tab-button" data-tab="nutrient-balance">Nutrient Balance</button>
                <button class="tab-button" data-tab="results">Results</button>
            </div>

            <!-- Site Information Tab -->
            <div class="tab-content active" id="site-info">
                <h3>Site Information</h3>
                <div class="form-group">
                    <label for="address">Site Address</label>
                    <input type="text" id="address" placeholder="Enter the site address" required>
                </div>
                
                <div class="form-grid">
                    <div class="form-group">
                        <label for="lat">Latitude</label>
                        <input type="text" id="lat" readonly>
                    </div>
                    <div class="form-group">
                        <label for="lng">Longitude</label>
                        <input type="text" id="lng" readonly>
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="irrigation-area">Irrigation Area (ha)</label>
                    <input type="number" id="irrigation-area" min="0" step="0.01" required>
                </div>
                
                <div class="form-group">
                    <label for="land-use">Land Use</label>
                    <select id="land-use" required>
                        <option value="">Select Land Use</option>
                        <option value="Forest 100%">Forest 100%</option>
                        <option value="Forest 80% Grass 20%">Forest 80% Grass 20%</option>
                        <option value="Forest 60% Grass 40%">Forest 60% Grass 40%</option>
                        <option value="Forest 40% Grass 60%">Forest 40% Grass 60%</option>
                        <option value="Forest 20% Grass 80%">Forest 20% Grass 80%</option>
                        <option value="Grass 100%">Grass 100%</option>
                        <option value="Crop 100%">Crop 100%</option>
                        <option value="Soil 100%">Soil 100%</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="land-slope">Land Slope (%)</label>
                    <select id="land-slope" required>
                        <option value="">Select Land Slope</option>
                        <option value="0-1%">0-1%</option>
                        <option value="1-3%">1-3%</option>
                        <option value="3-5%">3-5%</option>
                        <option value="5-10%">5-10%</option>
                        <option value="10-20%">10-20%</option>
                        <option value=">20%">>20%</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="ground-water">Ground Water Depth</label>
                    <div style="display: flex; gap: 10px;">
                        <input type="number" id="ground-water" min="0" step="0.01" style="flex: 3;" required>
                        <select id="ground-water-unit" style="flex: 1;">
                            <option value="m bgl">m bgl</option>
                            <option value="cm bgl">cm bgl</option>
                        </select>
                    </div>
                </div>
                
                <button class="btn" onclick="findCoordinates()">Get Coordinates</button>
                <button class="btn btn-accent" onclick="goToNextTab()">Next: Soil Data</button>
            </div>

            <!-- Soil Data Tab -->
            <div class="tab-content" id="soil-data">
                <h3>Soil Data</h3>
                
                <div class="form-group">
                    <table id="soil-layers-table">
                        <thead>
                            <tr>
                                <th>Layer</th>
                                <th>Depth From (m)</th>
                                <th>Depth To (m)</th>
                                <th>Soil Type</th>
                                <th>Soil Texture</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>1</td>
                                <td><input type="number" min="0" step="0.01" class="depth-from" value="0"></td>
                                <td><input type="number" min="0" step="0.01" class="depth-to"></td>
                                <td>
                                    <select class="soil-type">
                                        <option value="">Select Soil Type</option>
                                        <option value="Sand">Sand</option>
                                        <option value="Loamy Sand">Loamy Sand</option>
                                        <option value="Sandy Loam">Sandy Loam</option>
                                        <option value="Loam">Loam</option>
                                        <option value="Silty Loam">Silty Loam</option>
                                        <option value="Silt">Silt</option>
                                        <option value="Sandy Clay Loam">Sandy Clay Loam</option>
                                        <option value="Clay Loam">Clay Loam</option>
                                        <option value="Silty Clay Loam">Silty Clay Loam</option>
                                        <option value="Sandy Clay">Sandy Clay</option>
                                        <option value="Silty Clay">Silty Clay</option>
                                        <option value="Clay">Clay</option>
                                    </select>
                                </td>
                                <td>
                                    <select class="soil-texture">
                                        <option value="">Select Soil Texture</option>
                                        <option value="Loose">Loose</option>
                                        <option value="Earthy or Porous">Earthy or Porous</option>
                                        <option value="Poorly Structured">Poorly Structured</option>
                                        <option value="Moderately Structured">Moderately Structured</option>
                                        <option value="Strongly Structured">Strongly Structured</option>
                                    </select>
                                </td>
                            </tr>
                            <tr>
                                <td>2</td>
                                <td><input type="number" min="0" step="0.01" class="depth-from" readonly></td>
                                <td><input type="number" min="0" step="0.01" class="depth-to"></td>
                                <td>
                                    <select class="soil-type">
                                        <option value="">Select Soil Type</option>
                                        <option value="Sand">Sand</option>
                                        <option value="Loamy Sand">Loamy Sand</option>
                                        <option value="Sandy Loam">Sandy Loam</option>
                                        <option value="Loam">Loam</option>
                                        <option value="Silty Loam">Silty Loam</option>
                                        <option value="Silt">Silt</option>
                                        <option value="Sandy Clay Loam">Sandy Clay Loam</option>
                                        <option value="Clay Loam">Clay Loam</option>
                                        <option value="Silty Clay Loam">Silty Clay Loam</option>
                                        <option value="Sandy Clay">Sandy Clay</option>
                                        <option value="Silty Clay">Silty Clay</option>
                                        <option value="Clay">Clay</option>
                                        <option value="N/A">N/A</option>
                                    </select>
                                </td>
                                <td>
                                    <select class="soil-texture">
                                        <option value="">Select Soil Texture</option>
                                        <option value="Loose">Loose</option>
                                        <option value="Earthy or Porous">Earthy or Porous</option>
                                        <option value="Poorly Structured">Poorly Structured</option>
                                        <option value="Moderately Structured">Moderately Structured</option>
                                        <option value="Strongly Structured">Strongly Structured</option>
                                        <option value="N/A">N/A</option>
                                    </select>
                                </td>
                            </tr>
                            <tr>
                                <td>3</td>
                                <td><input type="number" min="0" step="0.01" class="depth-from" readonly></td>
                                <td><input type="number" min="0" step="0.01" class="depth-to"></td>
                                <td>
                                    <select class="soil-type">
                                        <option value="">Select Soil Type</option>
                                        <option value="Sand">Sand</option>
                                        <option value="Loamy Sand">Loamy Sand</option>
                                        <option value="Sandy Loam">Sandy Loam</option>
                                        <option value="Loam">Loam</option>
                                        <option value="Silty Loam">Silty Loam</option>
                                        <option value="Silt">Silt</option>
                                        <option value="Sandy Clay Loam">Sandy Clay Loam</option>
                                        <option value="Clay Loam">Clay Loam</option>
                                        <option value="Silty Clay Loam">Silty Clay Loam</option>
                                        <option value="Sandy Clay">Sandy Clay</option>
                                        <option value="Silty Clay">Silty Clay</option>
                                        <option value="Clay">Clay</option>
                                        <option value="N/A">N/A</option>
                                    </select>
                                </td>
                                <td>
                                    <select class="soil-texture">
                                        <option value="">Select Soil Texture</option>
                                        <option value="Loose">Loose</option>
                                        <option value="Earthy or Porous">Earthy or Porous</option>
                                        <option value="Poorly Structured">Poorly Structured</option>
                                        <option value="Moderately Structured">Moderately Structured</option>
                                        <option value="Strongly Structured">Strongly Structured</option>
                                        <option value="N/A">N/A</option>
                                    </select>
                                </td>
                            </tr>
                            <tr>
                                <td>4</td>
                                <td><input type="number" min="0" step="0.01" class="depth-from" readonly></td>
                                <td><input type="number" min="0" step="0.01" class="depth-to"></td>
                                <td>
                                    <select class="soil-type">
                                        <option value="">Select Soil Type</option>
                                        <option value="Sand">Sand</option>
                                        <option value="Loamy Sand">Loamy Sand</option>
                                        <option value="Sandy Loam">Sandy Loam</option>
                                        <option value="Loam">Loam</option>
                                        <option value="Silty Loam">Silty Loam</option>
                                        <option value="Silt">Silt</option>
                                        <option value="Sandy Clay Loam">Sandy Clay Loam</option>
                                        <option value="Clay Loam">Clay Loam</option>
                                        <option value="Silty Clay Loam">Silty Clay Loam</option>
                                        <option value="Sandy Clay">Sandy Clay</option>
                                        <option value="Silty Clay">Silty Clay</option>
                                        <option value="Clay">Clay</option>
                                        <option value="N/A">N/A</option>
                                    </select>
                                </td>
                                <td>
                                    <select class="soil-texture">
                                        <option value="">Select Soil Texture</option>
                                        <option value="Loose">Loose</option>
                                        <option value="Earthy or Porous">Earthy or Porous</option>
                                        <option value="Poorly Structured">Poorly Structured</option>
                                        <option value="Moderately Structured">Moderately Structured</option>
                                        <option value="Strongly Structured">Strongly Structured</option>
                                        <option value="N/A">N/A</option>
                                    </select>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
                
                <div class="form-group">
                    <label for="root-depth">Root Depth</label>
                    <div style="display: flex; gap: 10px;">
                        <input type="number" id="root-depth" min="0" step="0.01" style="flex: 3;" required>
                        <select id="root-depth-unit" style="flex: 1;">
                            <option value="m bgl">m bgl</option>
                            <option value="cm bgl">cm bgl</option>
                        </select>
                    </div>
                </div>
                
                <button class="btn btn-secondary" onclick="goToPreviousTab()">Previous: Site Information</button>
                <button class="btn btn-accent" onclick="goToNextTab()">Next: Plant Data</button>
            </div>

            <!-- Plant Data Tab -->
            <div class="tab-content" id="plant-data">
                <h3>Plant Data</h3>
                
                <div class="form-group">
                    <label for="plant-name">Plant Name/Genera</label>
                    <input type="text" id="plant-name" required>
                </div>
                
                <div class="form-grid">
                    <div class="form-group">
                        <label for="stump-diameter">Stump Diameter</label>
                        <div style="display: flex; gap: 10px;">
                            <input type="number" id="stump-diameter" min="0" step="0.01" style="flex: 3;" required>
                            <select id="stump-diameter-unit" style="flex: 1;">
                                <option value="cm">cm</option>
                                <option value="mm">mm</option>
                                <option value="m">m</option>
                            </select>
                        </div>
                    </div>
                    
                    <div class="form-group">
                        <label for="plant-height">Plant Height</label>
                        <div style="display: flex; gap: 10px;">
                            <input type="number" id="plant-height" min="0" step="0.01" style="flex: 3;" required>
                            <select id="plant-height-unit" style="flex: 1;">
                                <option value="m">m</option>
                                <option value="cm">cm</option>
                            </select>
                        </div>
                    </div>
                </div>
                
                <div class="form-grid">
                    <div class="form-group">
                        <label for="plant-age">Plant Age (years)</label>
                        <input type="number" id="plant-age" min="0" step="0.01" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="stock-density">Stock Density</label>
                        <div style="display: flex; gap: 10px;">
                            <input type="number" id="stock-density" min="0" step="0.01" style="flex: 3;" required>
                            <select id="stock-density-unit" style="flex: 1;">
                                <option value="t/ha">t/ha</option>
                                <option value="t/km^2">t/km^2</option>
                                <option value="t/m^2">t/m^2</option>
                            </select>
                        </div>
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="litter-type">Litter Type</label>
                    <select id="litter-type" required>
                        <option value="">Select Litter Type</option>
                        <option value="Heavy">Heavy</option>
                        <option value="Moderate">Moderate</option>
                        <option value="Light">Light</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="grass-type">Grass Type (if applicable)</label>
                    <input type="text" id="grass-type">
                </div>
                
                <div class="form-group">
                    <label for="clippings">Clippings Management</label>
                    <select id="clippings">
                        <option value="Removed">Removed</option>
                        <option value="Left">Left</option>
                    </select>
                </div>
                
                <button class="btn btn-secondary" onclick="goToPreviousTab()">Previous: Soil Data</button>
                <button class="btn btn-accent" onclick="goToNextTab()">Next: Water Balance</button>
            </div>

            <!-- Water Balance Tab -->
            <div class="tab-content" id="water-balance">
                <h3>Water Balance</h3>
                
                <h4>Monthly Outflow Data (m³)</h4>
                <div class="form-group">
                    <table id="outflow-table">
                        <thead>
                            <tr>
                                <th>Year</th>
                                <th>Jan</th>
                                <th>Feb</th>
                                <th>Mar</th>
                                <th>Apr</th>
                                <th>May</th>
                                <th>Jun</th>
                                <th>Jul</th>
                                <th>Aug</th>
                                <th>Sep</th>
                                <th>Oct</th>
                                <th>Nov</th>
                                <th>Dec</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>Year 1</td>
                                <td><input type="number" min="0" step="0.01" class="outflow-data"></td>
                                <td><input type="number" min="0" step="0.01" class="outflow-data"></td>
                                <td><input type="number" min="0" step="0.01" class="outflow-data"></td>
                                <td><input type="number" min="0" step="0.01" class="outflow-data"></td>
                                <td><input type="number" min="0" step="0.01" class="outflow-data"></td>
                                <td><input type="number" min="0" step="0.01" class="outflow-data"></td>
                                <td><input type="number" min="0" step="0.01" class="outflow-data"></td>
                                <td><input type="number" min="0" step="0.01" class="outflow-data"></td>
                                <td><input type="number" min="0" step="0.01" class="outflow-data"></td>
                                <td><input type="number" min="0" step="0.01" class="outflow-data"></td>
                                <td><input type="number" min="0" step="0.01" class="outflow-data"></td>
                                <td><input type="number" min="0" step="0.01" class="outflow-data"></td>
                            </tr>
                        </tbody>
                    </table>
                    <button class="btn" style="margin-top: 10px;" onclick="addOutflowYear()">Add Year</button>
                </div>
                
                <button class="btn btn-secondary" onclick="goToPreviousTab()">Previous: Plant Data</button>
                <button class="btn btn-accent" onclick="goToNextTab()">Next: Nutrient Balance</button>
            </div>

            <!-- Nutrient Balance Tab -->
            <div class="tab-content" id="nutrient-balance">
                <h3>Nutrient Balance</h3>
                
                <h4>Water Quality Data</h4>
                <p>Enter nutrient concentration data for the irrigation water</p>
                
                <div class="form-group">
                    <table id="nutrient-data-table">
                        <thead>
                            <tr>
                                <th>Date</th>
                                <th>TN (mg/L)</th>
                                <th>TP (mg/L)</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td><input type="date" class="nutrient-date"></td>
                                <td><input type="number" min="0" step="0.01" class="nutrient-tn"></td>
                                <td><input type="number" min="0" step="0.01" class="nutrient-tp"></td>
                            </tr>
                        </tbody>
                    </table>
                    <button class="btn" style="margin-top: 10px;" onclick="addNutrientRow()">Add Row</button>
                </div>
                
                <h4>Nutrient Content</h4>
                <div class="form-grid">
                    <div class="form-group">
                        <label for="plant-n">Plant N Content (%)</label>
                        <input type="number" id="plant-n" min="0" max="100" step="0.01" value="0.5">
                    </div>
                    
                    <div class="form-group">
                        <label for="plant-p">Plant P Content (%)</label>
                        <input type="number" id="plant-p" min="0" max="100" step="0.01" value="0.05">
                    </div>
                    
                    <div class="form-group">
                        <label for="grass-n">Grass N Content (%)</label>
                        <input type="number" id="grass-n" min="0" max="100" step="0.01" value="0.4">
                    </div>
                    
                    <div class="form-group">
                        <label for="grass-p">Grass P Content (%)</label>
                        <input type="number" id="grass-p" min="0" max="100" step="0.01" value="0.04">
                    </div>
                    
                    <div class="form-group">
                        <label for="litter-n">Leaf Litter N Content (%)</label>
                        <input type="number" id="litter-n" min="0" max="100" step="0.01" value="0.3">
                    </div>
                    
                    <div class="form-group">
                        <label for="clippings-n">Grass Clippings N Content (%)</label>
                        <input type="number" id="clippings-n" min="0" max="100" step="0.01" value="0.3">
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="soil-pri">Soil PRI</label>
                    <input type="number" id="soil-pri" min="0" step="0.1" value="10">
                </div>
                
                <button class="btn btn-secondary" onclick="goToPreviousTab()">Previous: Water Balance</button>
                <button class="btn btn-accent" onclick="goToNextTab()">Next: Results</button>
            </div>

            <!-- Results Tab -->
            <div class="tab-content" id="results">
                <h3>Results</h3>
                <p>Click the button below to calculate your Nutrient and Irrigation Management Plan.</p>
                
                <button class="btn btn-accent" onclick="calculateResults()">Calculate Results</button>
                
                <div id="results-container" class="result-section">
                    <div class="alert alert-success">
                        <p>Calculations completed successfully!</p>
                    </div>
                    
                    <h3>Water Balance Results</h3>
                    <div class="card">
                        <table id="water-balance-table">
                            <thead>
                                <tr>
                                    <th>Month</th>
                                    <th>Precipitation (mm)</th>
                                    <th>Evapotranspiration (mm)</th>
                                    <th>Runoff (mm)</th>
                                    <th>Interception (mm)</th>
                                    <th>Irrigation (mm)</th>
                                    <th>Deep Infiltration (mm)</th>
                                </tr>
                            </thead>
                            <tbody id="water-balance-tbody">
                                <!-- Will be filled with JavaScript -->
                            </tbody>
                        </table>
                    </div>
                    
                    <h3>Soil Properties</h3>
                    <div class="card">
                        <table id="soil-properties-table">
                            <thead>
                                <tr>
                                    <th>Soil Layer</th>
                                    <th>Runoff Coefficient</th>
                                    <th>Field Capacity (%)</th>
                                    <th>Permanent Wilting Point (%)</th>
                                    <th>Available Water Capacity (%)</th>
                                    <th>Hydraulic Conductivity (mm/day)</th>
                                </tr>
                            </thead>
                            <tbody id="soil-properties-tbody">
                                <!-- Will be filled with JavaScript -->
                            </tbody>
                        </table>
                    </div>
                    
                    <h3>Plant Biomass</h3>
                    <div class="card">
                        <table id="biomass-table">
                            <tbody>
                                <tr>
                                    <td>Total Biomass (kg)</td>
                                    <td id="total-biomass">-</td>
                                </tr>
                                <tr>
                                    <td>Plant N Content (kg)</td>
                                    <td id="plant-n-content">-</td>
                                </tr>
                                <tr>
                                    <td>Plant P Content (kg)</td>
                                    <td id="plant-p-content">-</td>
                                </tr>
                                <tr>
                                    <td>Leaf Litter N Content (kg/yr)</td>
                                    <td id="litter-n-content">-</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    
                    <h3>Nutrient Balance</h3>
                    <div class="card">
                        <table id="nutrient-balance-table">
                            <tbody>
                                <tr>
                                    <td>Total N Loading (kg/yr)</td>
                                    <td id="total-n-loading">-</td>
                                </tr>
                                <tr>
                                    <td>Total P Loading (kg/yr)</td>
                                    <td id="total-p-loading">-</td>
                                </tr>
                                <tr>
                                    <td>Plant N Uptake (kg/yr)</td>
                                    <td id="plant-n-uptake">-</td>
                                </tr>
                                <tr>
                                    <td>Plant P Uptake (kg/yr)</td>
                                    <td id="plant-p-uptake">-</td>
                                </tr>
                                <tr>
                                    <td>Denitrification (kg/yr)</td>
                                    <td id="denitrification">-</td>
                                </tr>
                                <tr>
                                    <td>N Balance (kg/yr)</td>
                                    <td id="n-balance">-</td>
                                </tr>
                                <tr>
                                    <td>P Balance (kg/yr)</td>
                                    <td id="p-balance">-</td>
                                </tr>
                                <tr>
                                    <td>Years until P Saturation</td>
                                    <td id="p-saturation-years">-</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    
                    <h3>Soil Water Status</h3>
                    <div class="chart-container">
                        <canvas id="soil-water-chart"></canvas>
                    </div>
                    
                    <h3>Deep Infiltration Contributions</h3>
                    <div class="chart-container">
                        <canvas id="infiltration-chart"></canvas>
                    </div>
                </div>
                
                <button class="btn btn-secondary" onclick="goToPreviousTab()">Previous: Nutrient Balance</button>
            </div>
        </div>
    </div>

    <footer>
        <div class="container">
            <p>Environmental Engineering Innovations - Nutrient and Irrigation Management Plan &copy; 2025</p>
        </div>
    </footer>

    <!-- Include Chart.js -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.9.1/chart.min.js"></script>
    
    <script>
        // Tab navigation
        document.querySelectorAll('.tab-button').forEach(button => {
            button.addEventListener('click', () => {
                const tabId = button.getAttribute('data-tab');
                
                // Hide all tabs and remove active class
                document.querySelectorAll('.tab-content').forEach(tab => {
                    tab.classList.remove('active');
                });
                document.querySelectorAll('.tab-button').forEach(btn => {
                    btn.classList.remove('active');
                });
                
                // Show selected tab and add active class
                document.getElementById(tabId).classList.add('active');
                button.classList.add('active');
            });
        });
        
        // Move to next tab
        function goToNextTab() {
            const activeTab = document.querySelector('.tab-button.active');
            const nextTab = activeTab.nextElementSibling;
            
            if (nextTab) {
                nextTab.click();
            }
        }
        
        // Move to previous tab
        function goToPreviousTab() {
            const activeTab = document.querySelector('.tab-button.active');
            const prevTab = activeTab.previousElementSibling;
            
            if (prevTab) {
                prevTab.click();
            }
        }
        
        // Add another year to outflow table
        function addOutflowYear() {
            const tbody = document.querySelector('#outflow-table tbody');
            const rowCount = tbody.rows.length + 1;
            
            const newRow = document.createElement('tr');
            newRow.innerHTML = `
                <td>Year ${rowCount}</td>
                ${Array(12).fill('<td><input type="number" min="0" step="0.01" class="outflow-data"></td>').join('')}
            `;
            
            tbody.appendChild(newRow);
        }
        
        // Add another row to nutrient data table
        function addNutrientRow() {
            const tbody = document.querySelector('#nutrient-data-table tbody');
            
            const newRow = document.createElement('tr');
            newRow.innerHTML = `
                <td><input type="date" class="nutrient-date"></td>
                <td><input type="number" min="0" step="0.01" class="nutrient-tn"></td>
                <td><input type="number" min="0" step="0.01" class="nutrient-tp"></td>
            `;
            
            tbody.appendChild(newRow);
        }
        
        // Update depth-from based on previous depth-to
        document.querySelectorAll('.depth-to').forEach((input, index) => {
            input.addEventListener('change', () => {
                if (index < document.querySelectorAll('.depth-from').length - 1) {
                    const nextDepthFrom = document.querySelectorAll('.depth-from')[index + 1];
                    nextDepthFrom.value = input.value;
                }
            });
        });
        
        // Geocoding function
        function findCoordinates() {
            const addressInput = document.getElementById('address').value;
            
            if (!addressInput) {
                alert('Please enter an address');
                return;
            }
            
            // In a real implementation, we would call the Nominatim API here
            // For this demo, we'll simulate the API call
            
            // Simulate API delay
            document.getElementById('lat').value = 'Loading...';
            document.getElementById('lng').value = 'Loading...';
            
            setTimeout(() => {
                // These would normally come from the API
                // For the demo, let's use a fixed example (Sydney, Australia)
                document.getElementById('lat').value = '-33.8688';
                document.getElementById('lng').value = '151.2093';
                
                alert('Coordinates retrieved successfully!');
            }, 1000);
        }
        
        // Calculate results
        function calculateResults() {
            // In a real implementation, we would implement all the calculations from the VBA macros
            // For this demo, we'll simulate the results with sample data
            
            // Show results container
            document.getElementById('results-container').style.display = 'block';
            
            // Populate water balance table with sample data
            const waterBalanceTbody = document.getElementById('water-balance-tbody');
            waterBalanceTbody.innerHTML = '';
            
            const months = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'];
            
            // Sample data - in a real implementation this would come from calculations
            const sampleData = [
                {precip: 80, evap: 110, runoff: 12, intercept: 12, irrig: 40, deep: 0},
                {precip: 90, evap: 100, runoff: 14, intercept: 14, irrig: 40, deep: 2},
                {precip: 70, evap: 90, runoff: 11, intercept: 11, irrig: 35, deep: 0},
                {precip: 60, evap: 70, runoff: 9, intercept: 9, irrig: 30, deep: 4},
                {precip: 50, evap: 50, runoff: 8, intercept: 8, irrig: 25, deep: 9},
                {precip: 40, evap: 40, runoff: 6, intercept: 6, irrig: 20, deep: 8},
                {precip: 30, evap: 45, runoff: 5, intercept: 5, irrig: 25, deep: 0},
                {precip: 35, evap: 55, runoff: 5, intercept: 5, irrig: 30, deep: 0},
                {precip: 45, evap: 70, runoff: 7, intercept: 7, irrig: 35, deep: 0},
                {precip: 55, evap: 85, runoff: 8, intercept: 8, irrig: 35, deep: 0},
                {precip: 65, evap: 95, runoff: 10, intercept: 10, irrig: 40, deep: 0},
                {precip: 75, evap: 105, runoff: 11, intercept: 11, irrig: 40, deep: 0}
            ];
            
            months.forEach((month, i) => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${month}</td>
                    <td>${sampleData[i].precip.toFixed(1)}</td>
                    <td>${sampleData[i].evap.toFixed(1)}</td>
                    <td>${sampleData[i].runoff.toFixed(1)}</td>
                    <td>${sampleData[i].intercept.toFixed(1)}</td>
                    <td>${sampleData[i].irrig.toFixed(1)}</td>
                    <td>${sampleData[i].deep.toFixed(1)}</td>
                `;
                waterBalanceTbody.appendChild(row);
            });
            
            // Populate soil properties table
            const soilPropertiesTbody = document.getElementById('soil-properties-tbody');
            soilPropertiesTbody.innerHTML = '';
            
            // Sample soil data
            const soilData = [
                {layer: 'Layer 1', runoff: 0.35, fc: 28.0, pwp: 14.0, awc: 14.0, hc: 450},
                {layer: 'Layer 2', runoff: 0.30, fc: 32.0, pwp: 15.0, awc: 17.0, hc: 350},
                {layer: 'Layer 3', runoff: 0.40, fc: 38.0, pwp: 18.0, awc: 20.0, hc: 200},
                {layer: 'Layer 4', runoff: 0.45, fc: 40.0, pwp: 20.0, awc: 20.0, hc: 150}
            ];
            
            soilData.forEach(soil => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${soil.layer}</td>
                    <td>${soil.runoff.toFixed(2)}</td>
                    <td>${soil.fc.toFixed(1)}</td>
                    <td>${soil.pwp.toFixed(1)}</td>
                    <td>${soil.awc.toFixed(1)}</td>
                    <td>${soil.hc.toFixed(1)}</td>
                `;
                soilPropertiesTbody.appendChild(row);
            });
            
            // Populate biomass and nutrient data
            document.getElementById('total-biomass').textContent = '12,500.0';
            document.getElementById('plant-n-content').textContent = '62.5';
            document.getElementById('plant-p-content').textContent = '6.3';
            document.getElementById('litter-n-content').textContent = '7.5';
            
            document.getElementById('total-n-loading').textContent = '120.0';
            document.getElementById('total-p-loading').textContent = '12.0';
            document.getElementById('plant-n-uptake').textContent = '58.0';
            document.getElementById('plant-p-uptake').textContent = '5.8';
            document.getElementById('denitrification').textContent = '80.0';
            document.getElementById('n-balance').textContent = '-18.0';
            document.getElementById('p-balance').textContent = '6.2';
            document.getElementById('p-saturation-years').textContent = '45';
            
            // Create soil water status chart
            const soilWaterCtx = document.getElementById('soil-water-chart').getContext('2d');
            const soilWaterChart = new Chart(soilWaterCtx, {
                type: 'line',
                data: {
                    labels: months,
                    datasets: [
                        {
                            label: 'Total Soil Water',
                            data: [0.28, 0.29, 0.27, 0.25, 0.23, 0.21, 0.19, 0.17, 0.18, 0.19, 0.20, 0.22],
                            borderColor: 'rgba(54, 162, 235, 1)',
                            backgroundColor: 'rgba(54, 162, 235, 0.2)',
                            fill: false,
                            tension: 0.4
                        },
                        {
                            label: 'Field Capacity',
                            data: Array(12).fill(0.32),
                            borderColor: 'rgba(255, 99, 132, 1)',
                            backgroundColor: 'rgba(255, 99, 132, 0.2)',
                            borderDash: [5, 5],
                            fill: false
                        },
                        {
                            label: 'Lower Limit',
                            data: Array(12).fill(0.15),
                            borderColor: 'rgba(255, 159, 64, 1)',
                            backgroundColor: 'rgba(255, 159, 64, 0.2)',
                            borderDash: [5, 5],
                            fill: false
                        }
                    ]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            title: {
                                display: true,
                                text: 'Soil Water (m)'
                            }
                        }
                    }
                }
            });
            
            // Create infiltration chart
            const infiltrationCtx = document.getElementById('infiltration-chart').getContext('2d');
            const infiltrationChart = new Chart(infiltrationCtx, {
                type: 'bar',
                data: {
                    labels: months,
                    datasets: [
                        {
                            label: 'Rainfall Contribution',
                            data: [0, 1, 0, 2, 4, 3, 0, 0, 0, 0, 0, 0],
                            backgroundColor: 'rgba(54, 162, 235, 0.7)'
                        },
                        {
                            label: 'Irrigation Contribution',
                            data: [0, 1, 0, 2, 5, 5, 0, 0, 0, 0, 0, 0],
                            backgroundColor: 'rgba(75, 192, 192, 0.7)'
                        }
                    ]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            title: {
                                display: true,
                                text: 'Deep Infiltration (mm)'
                            },
                            stacked: true
                        },
                        x: {
                            stacked: true
                        }
                    }
                }
            });
            
            // Scroll to results
            document.getElementById('results-container').scrollIntoView({ behavior: 'smooth' });
        }
    </script>
</body>
</html>
